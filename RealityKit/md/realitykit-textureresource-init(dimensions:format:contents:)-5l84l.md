

- RealityKit
- TextureResource
-  init(dimensions:format:contents:) 

Initializer

# init(dimensions:format:contents:)

Synchronously creates a 3D texture resource from a pixel Metal buffer, or data.

iOS 18.0+iPadOS 18.0+Mac Catalyst 18.0+macOS 15.0+visionOS 2.0+

``` source
@MainActor @preconcurrency
convenience init(
    dimensions: TextureResource.Dimensions3D,
    format: TextureResource.Format,
    contents: TextureResource.Contents
) throws
```

## Parameters 

`dimensions`  

The dimensions of the 3D texture to create.

`format`  

The semantic interpretation of the pixel data.

`contents`  

Pixel data the system copies into the created texture.

## Discussion

RealityKit efficiently creates a 3D texture from raw pixel bytes, with full control over the values and pixel format. See init(dimensions:format:contents:) for more details.

Loading a TextureResource with this method blocks the main actor because it’s synchronous, so only call it from a command-line application. The method can stall a regular app, which makes it visibly hitch, and the system terminates an app if its UI becomes unresponsive. See init(named:in:) for an example that demonstrates how to safely load content.

## See Also

### Creating a 3D texture resource

static func texture3D(slices: [CGImage], named: String?, options: TextureResource.CreateOptions) async throws -> TextureResource

Asynchronously creates a 3D texture by generating it from images.

static func texture3D(slices: [CGImage], named: String?, options: TextureResource.CreateOptions) throws -> TextureResource

Synchronously creates a 3D texture by generating it from images.

convenience init(dimensions: TextureResource.Dimensions3D, format: TextureResource.Format, contents: TextureResource.Contents) async throws

Asynchronously creates a 3D texture resource from a pixel Metal buffer, or data.

struct Dimensions3D

The dimensions of the 3D texture.

