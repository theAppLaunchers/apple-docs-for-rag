

- Metal
- Render Passes
-  Scaling Variable Rasterization Rate Content 

Article

# Scaling Variable Rasterization Rate Content

Use the rate map data to scale the content to fill your destination texture.

## Overview

At some point in the rendering process, you need to scale your content up to a full-rate image. Most often, this means performing a render or compute pass that reads the pixel data from the intermediate texture and copies or transforms it to generate the final target texture. Scaling the content might be your final step, or you might follow the scaling process with additional work on the full-rate image. For example, you should usually render text and user-interface elements at the full rate on top of the scaled image.

### Copy the Rate Map Data into a Metal Buffer

You do the rate conversions in a fragment shader. First, copy the rate map’s transformation data into a Metal buffer and then send that data to the shader.

The following example code asks the rate map for the size of its internal rate data, allocates a Metal buffer just for that data, and copies the data into the buffer.

- Swift
- Objective-C

```
// Create a buffer for the rate map.
let rateMapParamSize = rateMap.parameterDataSizeAndAlign
if let rateMapData = device.makeBuffer(length: rateMapParamSize.size,
                                       options: MTLResourceOptions.storageModeShared) {
    // Copy the rate map's data into the buffer.
    rateMap.copyParameterData(buffer: rateMapData, offset: 0)
}
```

```
// Create a buffer for the rate map.
MTLSizeAndAlign rateMapParamSize = _rateMap.parameterBufferSizeAndAlign;
_rateMapData = [_device newBufferWithLength: rateMapParamSize.size
                          options:MTLResourceStorageModeShared];

// Copy the rate map's data into the buffer.
[_rateMap copyParameterDataToBuffer:_rateMapData offset:0];
```

You need to reserve enough space in the buffer for the data, and specify an offset that’s a multiple of the alignment value returned by parameterDataSizeAndAlign. You can copy the data into a Metal buffer that contains other data.

Pass the buffer as an argument to your shader when you encode the command to draw the scaled data:

- Swift
- Objective-C

```
renderEncoder.setFragmentBuffer(rateMapData, offset: 0, index: 0)
```

```
[renderEncoder setFragmentBuffer:_rateMapData offset:0 atIndex:0];
```

### Convert Between Screen and Physical Coordinates

Metal Shading Language provides functions that work with the rate map data to convert between screen (logical viewport) coordinates and physical texture coordinates. The fragment shader below scales the intermediate texture and copies it into the destination texture. It passes the rate map data you provided to a rate map decoder object and uses that object to convert the target screen coordinates to physical coordinates in the intermediate texture. Then it samples that location and returns the result.

```
typedef struct
{
    float4 position [[position]];
} PassThroughVertexOutput;

fragment float4 transformMappedToScreenFragments(
        PassThroughVertexOutput in [[stage_in]],
        constant rasterization_rate_map_data &data [[buffer(0)]],
        texture2d intermediateColorMap    [[ texture(0) ]])

{
    constexpr sampler s(coord::pixel, address::clamp_to_edge, filter::linear);

    rasterization_rate_map_decoder map(data);
    float2 physCoords = map.map_screen_to_physical_coordinates(in.position.xy);

    return float4(intermediateColorMap.sample(s, physCoords));

}
```

In iOS, you don’t usually create a separate render pass just to scale an image. Instead, to reduce memory bandwidth usage, combine this render pass with other rendering that follows the scaling process.

## See Also

### Rasterization Settings

Rendering at Different Rasterization Rates

Configure a rasterization rate map to vary rasterization rates depending on the amount of detail needed.

Creating a Rasterization Rate Map

Define the rasterization rates for each part of your render target.

Rendering with a Rasterization Rate Map

Create offscreen textures to hold intermediate rasterized data.

class MTLRasterizationRateMapDescriptor

An object that you use to configure new rasterization rate maps.

protocol MTLRasterizationRateMap

A compiled read-only object that determines how to apply variable rasterization rates when rendering.

typealias MTLCoordinate2D

A coordinate in the viewport.

func MTLCoordinate2DMake(Float, Float) -> MTLCoordinate2D

Returns a new 2D point with the specified coordinates.

