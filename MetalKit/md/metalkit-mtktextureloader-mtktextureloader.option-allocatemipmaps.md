

- MetalKit
- MTKTextureLoader
- MTKTextureLoader.Option
-  allocateMipmaps 

Type Property

# allocateMipmaps

A key used to specify whether the texture loader should allocate memory for mipmaps in the texture.

iOS 9.0+iPadOS 9.0+Mac Catalyst 13.1+macOS 10.11+tvOS 9.0+visionOS 1.0+

``` source
static let allocateMipmaps: MTKTextureLoader.Option
```

## Discussion

The value for this key is an NSNumber object containing a boolean value.

This option applies only if the texture being loaded does not contain mipmap data. When loading such a texture, if the value is false, only the texture is loaded and its mipmap contents are undefined. If the value is true, a full set of mipmap levels are allocated for the texture when the texture is loaded, and it is your responsibility to generate the mipmap contents. If this key is not specified and the image being loaded contains data for mipmaps, the mipmap memory is allocated and the image data is loaded.

Note

This option only allocates mipmap memory for the texture. To generate the actual mipmaps for the texture, use the generateMipmaps option and set it to true.

## See Also

### Specifying Mipmap Options

static let generateMipmaps: MTKTextureLoader.Option

A key used to specify whether the texture loader should generate mipmaps for the texture.

