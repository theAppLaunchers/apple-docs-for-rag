

- RealityKit
- Materials, textures, and shaders
-  Creating a dynamic height and normal map with low-level texture 

Article

# Creating a dynamic height and normal map with low-level texture

Create a low-level texture and update its pixel data on the GPU to form a dynamic height and normal map.

## Overview

A height map is a texture in which each pixel stores height information describing the shape of a surface. You can read height data from a height map to offset the vertices of a mesh, as well as derive the surface normal directions. Generally speaking, height maps are static textures that remain unmodified at runtime; however, by leveraging LowLevelTexture, you can create a dynamic height map that you write height data to in every frame on the GPU. Additionally, you can derive surface normals from your height map every time you update it, allowing for a variety of dynamic and interactive effects.

Create a height map with LowLevelTexture, and write height data to its alpha channel in every frame by dispatching a Metal compute shader. Derive normal directions from the height map and store them in the red, green, and blue channels of the texture. See Generating interactive geometry with RealityKit for an example of how you can dynamically modify the vertices of a low-level mesh with this height and normal map texture.

## Create a low-level texture

Create a height map LowLevelTexture by describing its pixel format, width, height, and usage:

```
/// The low-level texture that stores the height and normal information of the height map.
var heightMapTexture: LowLevelTexture

init(dimensions: SIMD2) throws {
    // Initialize the texture with an RGBA pixel format where the alpha channel stores height,
    // while the red, green, and blue channels store the surface normal direction.
    let textureDescriptor = LowLevelTexture.Descriptor(pixelFormat: .rgba32Float,
                                                       width: Int(dimensions.x),
                                                       height: Int(dimensions.y),
                                                       textureUsage: [.shaderRead, .shaderWrite])
    self.heightMapTexture = try LowLevelTexture(descriptor: textureDescriptor)
}
```

Initialize this texture with a pixel format of MTLPixelFormat.rgba32Float so that each pixel in the texture has four 32-bit floats, composing its red, green, blue, and alpha channels. You can store height in the alpha channel, and the surface normal direction in the red, green, and blue channels.

## Write height data to the low-level texture with a compute shader

Write height data to the texture on the GPU by dispatching a Metal compute shader. For example, you can create a height map with waves that oscillate outward from the center of the texture by setting the height of each pixel to the sine of the pixel’s distance from the center:

```
/// Generates a height map in the shape of a sine wave moving outward from the center of the texture.
[[kernel]]
void generateSineWaveHeightMap(texture2d heightMapIn [[texture(0)]],
                               texture2d heightMapOut [[texture(1)]],
                               constant float &time [[buffer(2)]],
                               constant float &amplitude [[buffer(3)]],
                               uint2 pixelCoords [[thread_position_in_grid]]) {
    // Skip out-of-bounds threads.
    // https://developer.apple.com/documentation/metal/compute_passes/calculating_threadgroup_and_grid_sizes
    if (pixelCoords.x >= heightMapIn.get_width() || pixelCoords.y >= heightMapIn.get_height()) { return; }

    // Compute texture coordinates ranging from 0 to 1 along each axis.
    float2 uv = float2(pixelCoords.x / (heightMapIn.get_width() - 1.0),
                       pixelCoords.y / (heightMapIn.get_height() - 1.0));

    // Get the distance to the center of the texture in texture coordinate space.
    float distanceToCenter = length(uv - 0.5);
    // Normalize the distance to a range from 0 to 2π along the horizontal and vertical axes.
    float normalizedDistanceToCenter = (distanceToCenter / 0.5) * (2 * M_PI_F);

    // Get sine as a function of the normalized distance to the center of the texture times the wave count,
    // subtracting time to animate it outward over time.
    float waveCount = 3;
    float sine = sin(normalizedDistanceToCenter * waveCount - time);
    // Convert sine to the range 0 to 1.
    float sine01 = (sine + 1) / 2;

    // Generate height from the sine function.
    float height = amplitude * sine01;

    // Read the current height map data.
    float4 heightMapData = heightMapIn.read(pixelCoords);
    // Update the alpha channel with the new height.
    heightMapData.a = height;
    // Write the updated height data to height map.
    heightMapOut.write(heightMapData, pixelCoords);
}
```

Include the height map texture as a parameter of this function twice, both in a readable and a writable format, so that you can update the alpha channel of each pixel without updating the red, green, and blue channels.

The following video shows the alpha channel of texture this compute shader function creates:

 Video with custom controls. 

 Content description: A video of the height map texture the generate sine wave height map compute shader function creates. The texture oscillates from black to white in concentric circles growing outward from the center of the texture over time. 

Play 

## Dispatch the compute shader

Create a helper method that makes the MTLComputePipelineState for a given compute shader function:

```
/// The device Metal selects as the default.
let metalDevice: MTLDevice? = MTLCreateSystemDefaultDevice()

/// Makes a compute pipeline for the compute function with the given name.
func makeComputePipeline(named name: String) -> MTLComputePipelineState? {
    guard let function = metalDevice?.makeDefaultLibrary()?.makeFunction(name: name) else {
        return nil
    }
    return try? metalDevice?.makeComputePipelineState(function: function)
}
```

Get the MTLComputePipelineState for the `generateSineWaveHeightMap` compute shader function:

```
private let sineWaveHeightPipeline: MTLComputePipelineState = makeComputePipeline(named: "generateSineWaveHeightMap")!
```

Next, calculate the number of threads and threadgroups to dispatch:

```
let threadWidth = sineWaveHeightPipeline.threadExecutionWidth
let threadHeight = sineWaveHeightPipeline.maxTotalThreadsPerThreadgroup / threadWidth
let threadsPerThreadgroup = MTLSize(width: threadWidth, height: threadHeight, depth: 1)
let threadgroups = MTLSize(width: (Int(dimensions.x) + threadWidth - 1) / threadWidth,
                           height: (Int(dimensions.y) + threadHeight - 1) / threadHeight,
                           depth: 1)
```

Then, define the time and amplitude parameters:

```
private var time: Float = 0
private var amplitude: Float = 0.05
```

Finally, dispatch the `generateSineWaveHeightMap` function in every frame with an MTLComputeCommandEncoder, passing it both a readable and a writable version of the height map LowLevelTexture, as well as the time and the amplitude:

```
// Increment time.
time += deltaTime

// Set the compute shader pipeline to `generateSineWaveHeightMap`.
computeEncoder.setComputePipelineState(sineWaveHeightPipeline)

// Pass a readable version of the height map texture to the compute shader.
computeEncoder.setTexture(heightMapTexture.read(), index: 0)
// Pass a writable version of the height map texture to the compute shader.
computeEncoder.setTexture(heightMapTexture.replace(using: commandBuffer), index: 1)

// Pass the time to the compute shader.
computeEncoder.setBytes(&time, length: MemoryLayout.size, index: 2)
// Pass the amplitude to the compute shader.
computeEncoder.setBytes(&amplitude, length: MemoryLayout.size, index: 3)

// Dispatch the compute shader.
computeEncoder.dispatchThreadgroups(threadgroups, threadsPerThreadgroup: threadsPerThreadgroup)
```

See Performing Calculations on a GPU for general information about dispatching Metal shaders, as well as Passing Metal command objects around your application for specifics on how to obtain the compute encoder, command buffer, and delta time parameters.

## Derive surface normals from the height map texture

You can derive surface normal directions directly from the height map and store them in its red, green, and blue channels.

Note

The Generating interactive geometry with RealityKit sample sets its vertex normals with the normals the height map texture stores.

Derive the normal direction at each pixel in the height map by computing the difference between the pixel’s neighboring height values:

```
/// Derives normal directions from a height map, storing them in the texture's rgb channels.
[[kernel]]
void deriveNormalsFromHeightMap(texture2d heightMapIn [[texture(0)]],
                                texture2d heightMapOut [[texture(1)]],
                                constant float2 &cellSize [[buffer(2)]],
                                uint2 pixelCoords [[thread_position_in_grid]]) {
    // Get the dimensions of the height map.
    uint2 dimensions = uint2(heightMapIn.get_width(), heightMapIn.get_height());

    // Skip out-of-bounds threads.
    if (any(pixelCoords >= dimensions)) { return; }

    // The current pixel coordinate minus one in both dimensions, guaranteed to be in bounds.
    uint2 pixelCoordsMinusOne = max(pixelCoords, 1) - 1;
    // The current pixel coordinate plus one in both dimensions, guaranteed to be in bounds.
    uint2 pixelCoordsPlusOne = min(pixelCoords + 1, dimensions - 1);

    // Sample the current pixel along with its four neighbors.
    float height = heightMapIn.read(pixelCoords).a;
    float leftHeight = heightMapIn.read(uint2(pixelCoordsMinusOne.x, pixelCoords.y)).a;
    float rightHeight = heightMapIn.read(uint2(pixelCoordsPlusOne.x, pixelCoords.y)).a;
    float bottomHeight = heightMapIn.read(uint2(pixelCoords.x, pixelCoordsMinusOne.y)).a;
    float topHeight = heightMapIn.read(uint2(pixelCoords.x, pixelCoordsPlusOne.y)).a;

    // Compute the normal direction using central differences.
    float3 normal = normalize(float3((leftHeight - rightHeight) / (cellSize.x * 2),
                                     (bottomHeight - topHeight) / (cellSize.y * 2),
                                     1));

    // Write the normal direction to the height map.
    heightMapOut.write(float4(normal, height), pixelCoords);
}
```

Get the MTLComputePipelineState for this compute function:

```
private let deriveNormalsPipeline: MTLComputePipelineState = makeComputePipeline(named: "deriveNormalsFromHeightMap")!
```

Finally, dispatch this compute function with an MTLComputeCommandEncoder, passing in both a readable and a writable version of the height map low-level texture:

```
// Set the compute shader pipeline to `deriveNormalsFromHeightMap`.
computeEncoder.setComputePipelineState(deriveNormalsPipeline)

// Pass a readable version of the height map texture to the compute shader.
computeEncoder.setTexture(heightMapTexture.read(), index: 0)
// Pass a writable version of the height map texture to the compute shader.
computeEncoder.setTexture(heightMapTexture.replace(using: commandBuffer), index: 1)

// Pass the cell size to the compute shader.
computeEncoder.setBytes(&cellSize, length: MemoryLayout>.size, index: 2)

// Dispatch the compute shader.
computeEncoder.dispatchThreadgroups(threadgroups, threadsPerThreadgroup: threadsPerThreadgroup)
```

In this example, `cellSize` describes the size of the texture’s pixels in the same units as the height. In the Generating interactive geometry with RealityKit sample, this is the size of the cells that compose the plane mesh, or rather the distance between the vertices of the mesh.

The following video shows the normal map the compute shader function derives from the sine wave height map:

 Video with custom controls. 

 Content description: A video of the normal map texture the compute shader derives from the sine wave height map. Concentric circles of light teal, pink, blue, and purple oscillate outward in a gradient over time. 

Play 

## See Also

### Texture drawing

Rendering a windowed game in stereo

Bring an iOS or iPadOS game to visionOS and enhance it.

class LowLevelTexture

A container for texture data allowing you to create and update textures using your own format.

struct Descriptor

An object that you use to configure new `LowLevelTexture` objects.

class Drawable

A drawable associated with a drawable queue

class DrawableQueue

A drawable queue that may be used to update a texture resource dynamically

struct Descriptor

Describes the texture managed by the drawable queue

