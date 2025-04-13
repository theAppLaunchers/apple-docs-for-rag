

- RealityKit
- TextureResource
-  texture2DArray(slices:named:options:) 

Type Method

# texture2DArray(slices:named:options:)

Synchronously creates a 2D texture array by generating it from images.

iOS 18.0+iPadOS 18.0+Mac Catalyst 18.0+macOS 15.0+visionOS 2.0+

``` source
@MainActor @preconcurrency
static func texture2DArray(
    slices: [CGImage],
    named resourceName: String? = nil,
    options: TextureResource.CreateOptions
) throws -> TextureResource
```

## Parameters 

`slices`  

The source images, one per 2D array index. All images need to have the same size and format.

`resourceName`  

A unique name for syncing the texture resource across the network. The name is empty if you don’t include one.

`options`  

A configuration for generating the texture.

## Discussion

RealityKit creates a MTLTextureType.type2DArray texture with`'arrayLength == slices.count` from an array of images.

You can assign the resulting texture to a material you create in Reality Composer Pro that requires a 2D texture array.

Loading a TextureResource with this method blocks the main actor because it’s synchronous, so only call it from a command-line application. The method can stall a regular app, which makes it visibly hitch, and the system terminates an app if its UI becomes unresponsive. See init(named:in:) for an example that demonstrates how to safely load content.

```
// Create a 2D array texture from image slices.
let texture2DArray = try await TextureResource.texture2DArray(
    slices: [image0, image1, image2],
    options: TextureResource.CreateOptions(semantic: .color))

// Assign the 2D array texture to a compatible shader graph material parameter.
var material = try await ShaderGraphMaterial(
    named: "/Root/Spaceship/MaterialWith2DArray", from: url)

try material.setParameter(
    name: "input2DArray", value: .textureResource(texture2DArray))
```

## See Also

### Creating a 2D array texture resource

static func texture2DArray(slices: [CGImage], named: String?, options: TextureResource.CreateOptions) async throws -> TextureResource

Asynchronously creates a 2D texture array by generating it from images.

convenience init(dimensions: TextureResource.Dimensions2DArray, format: TextureResource.Format, contents: TextureResource.Contents) async throws

Asynchronously creates a 2D array texture resource from a pixel Metal buffer, or data.

convenience init(dimensions: TextureResource.Dimensions2DArray, format: TextureResource.Format, contents: TextureResource.Contents) throws

Synchronously creates a 2D array texture resource from a pixel Metal buffer, or data.

struct Dimensions2DArray

The dimensions of the 2D array texture.

