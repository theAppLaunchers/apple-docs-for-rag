

- Model I/O
- MDLTextureFilter
-  mipFilter 

Instance Property

# mipFilter

The filter mode for rendering textures using mipmapping.

iOS 9.0+iPadOS 9.0+Mac Catalyst 13.1+macOS 10.11+tvOS 9.0+visionOS 1.0+

``` source
var mipFilter: MDLMaterialMipMapFilterMode { get set }
```

## Discussion

Mipmapping is a technique that can increase rendering performance when rendering a texture image at smaller sizes. A texture can contain several mipmap levels for its image contents, each at a fraction of the original image’s size. A renderer samples texels from the mipmap level closest to the size being rendered.

The default value is MDLMaterialMipMapFilterMode.linear, indicating that a renderer should linearly interpolate between mipmap levels.

## See Also

### Managing Texture Filter Modes

var minFilter: MDLMaterialTextureFilterMode

The filter mode for rendering textures at sizes smaller than that of the original image.

var magFilter: MDLMaterialTextureFilterMode

The filter mode for rendering textures at sizes larger than that of the original image.

