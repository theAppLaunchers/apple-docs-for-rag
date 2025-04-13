

- RealityKit
- TextureResource
-  init(dimensions:format:contents:) 

Initializer

# init(dimensions:format:contents:)

Asynchronously creates a 3D texture resource from a pixel Metal buffer, or data.

iOS 18.0+iPadOS 18.0+Mac Catalyst 18.0+macOS 15.0+visionOS 2.0+

``` source
@MainActor @preconcurrency
convenience init(
    dimensions: TextureResource.Dimensions3D,
    format: TextureResource.Format,
    contents: TextureResource.Contents
) async throws
```

## Parameters 

`dimensions`  

The dimensions of the 3D texture to create.

`format`  

The semantic interpretation of the pixel data.

`contents`  

Pixel data the system copies into the created texture.

## Discussion

RealityKit efficiently creates a 3D texture from raw pixel bytes, with full control over the values and pixel format. You can assign the resulting texture to a material you create in Reality Composer Pro that requires a 3D texture.

```
var mips: [TextureResource.Contents.MipmapLevel] = []

// Create the various mipmap levels.
// A `bufferMipsInfo` structure describes the mipmap packing in the source `MTLBuffer`.
for mipInfo in bufferMipsInfo {
    // A mipmap contains all of the depth slices,
    // each with a stride that `bytesPerImage` specifies.
    mips.append(.mip(
        unsafeBuffer: buffer,
        offset: mipInfo.offset,
        size: mipInfo.size,
        bytesPerRow: mipInfo.width * bytesPerPixel,
        bytesPerImage: mipInfo.width * mipInfo.height * bytesPerPixel
    ))
}

let texture = try TextureResource(
    dimensions: .dimensions(width: width, height: height, depth: depth),
    format: .color(.displayP3, pixelFormat: .rgba8Unorm),
    contents: TextureResource.Contents(mipmapLevels: mips)
)
```

See init(named:in:) for an example of optimally loading textures with other content.

## See Also

### Creating a 3D texture resource

static func texture3D(slices: [CGImage], named: String?, options: TextureResource.CreateOptions) async throws -> TextureResource

Asynchronously creates a 3D texture by generating it from images.

static func texture3D(slices: [CGImage], named: String?, options: TextureResource.CreateOptions) throws -> TextureResource

Synchronously creates a 3D texture by generating it from images.

convenience init(dimensions: TextureResource.Dimensions3D, format: TextureResource.Format, contents: TextureResource.Contents) throws

Synchronously creates a 3D texture resource from a pixel Metal buffer, or data.

struct Dimensions3D

The dimensions of the 3D texture.

