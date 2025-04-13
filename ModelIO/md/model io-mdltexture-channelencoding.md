

- Model I/O
- MDLTexture
-  channelEncoding 

Instance Property

# channelEncoding

The data format for each channel value per texel.

iOS 9.0+iPadOS 9.0+Mac Catalyst 13.1+macOS 10.11+tvOS 9.0+visionOS 1.0+

``` source
var channelEncoding: MDLTextureChannelEncoding { get }
```

## Discussion

For example, each channel value for a texel may be an 8-bit integer or a 32-bit floating point value. For possible channel encodings, see MDLTextureChannelEncoding.

## See Also

### Examining Texture Attributes

var dimensions: vector_int2

The width and height, in texels, of the texture image.

var rowStride: Int

The number of bytes between the first texel in a row of image data and the first texel in the next row.

var channelCount: Int

The number of channels per texel.

var isCube: Bool

A Boolean value that indicates whether the texture is a cube textures.

var mipLevelCount: Int

The number of mipmap levels contained in the texture image data.

