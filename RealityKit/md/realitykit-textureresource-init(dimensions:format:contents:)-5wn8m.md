

- RealityKit
- TextureResource
-  init(dimensions:format:contents:) 

Initializer

# init(dimensions:format:contents:)

Asynchronously creates a 2D texture resource from a pixel Metal buffer, or data.

iOS 18.0+iPadOS 18.0+Mac Catalyst 18.0+macOS 15.0+visionOS 1.0+

``` source
@MainActor @preconcurrency
convenience init(
    dimensions: TextureResource.Dimensions2D,
    format: TextureResource.Format,
    contents: TextureResource.Contents
) async throws
```

## Parameters 

`dimensions`  

The width and height of the texture to create.

`format`  

The semantic interpretation of the pixel data.

`contents`  

Pixel data the system copies into the created texture.

## Discussion

RealityKit efficiently creates a 2D texture from raw pixel bytes, with full control over the values and pixel format.

```
var mips: [TextureResource.Contents.MipmapLevel] = []

// Create the various mipmap levels.
// A `bufferMipsInfo` structure describes the mipmap packing in the source `MTLBuffer`.
for mipInfo in bufferMipsInfo {
    mips.append(.mip(
        unsafeBuffer: buffer,
        offset: mipInfo.offset,
        size: mipInfo.size,
        bytesPerRow: mipInfo.width * bytesPerPixel
    ))
}

let texture = try await TextureResource(
    dimensions: .dimensions(width: width, height: height),
    format: .color(.displayP3, pixelFormat: .rgba8Unorm),
    contents: TextureResource.Contents(mipmapLevels: mips)
)
```

See init(named:in:) for an example of optimally loading textures with other content.

## See Also

### Creating a 2D texture resource

convenience init(image: CGImage, withName: String?, options: TextureResource.CreateOptions) async throws

Asynchronously creates a texture resource from an in-memory Core Graphics image.

convenience init(image: CGImage, withName: String?, options: TextureResource.CreateOptions) throws

Synchronously creates a texture resource from an in-memory Core Graphics image.

convenience init(dimensions: TextureResource.Dimensions2D, format: TextureResource.Format, contents: TextureResource.Contents) throws

Synchronously creates a 2D texture resource from a pixel Metal buffer, or data.

struct Dimensions2D

The dimensions of a 2D texture.

