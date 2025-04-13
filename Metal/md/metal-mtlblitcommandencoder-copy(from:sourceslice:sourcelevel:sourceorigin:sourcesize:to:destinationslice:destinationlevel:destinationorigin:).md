

- Metal
- MTLBlitCommandEncoder
-  copy(from:sourceSlice:sourceLevel:sourceOrigin:sourceSize:to:destinationSlice:destinationLevel:destinationOrigin:) 

Instance Method

# copy(from:sourceSlice:sourceLevel:sourceOrigin:sourceSize:to:destinationSlice:destinationLevel:destinationOrigin:)

Encodes a command that copies image data from a texture’s slice into another slice.

iOS 8.0+iPadOS 8.0+Mac Catalyst 13.1+macOS 10.11+tvOSvisionOS 1.0+

``` source
func copy(
    from sourceTexture: any MTLTexture,
    sourceSlice: Int,
    sourceLevel: Int,
    sourceOrigin: MTLOrigin,
    sourceSize: MTLSize,
    to destinationTexture: any MTLTexture,
    destinationSlice: Int,
    destinationLevel: Int,
    destinationOrigin: MTLOrigin
)
```

**Required**

## Parameters 

`sourceTexture`  

A texture with an isFramebufferOnly property value of false that the command copies data from.

For a texture that uses a compressed pixel format, align the copy region (`sourceOrigin` and `sourceSize`) to the pixel format’s block size.

`sourceSlice`  

A slice within `sourceTexture`.

`sourceLevel`  

A mipmap level within `sourceTexture`.

`sourceOrigin`  

A location within `sourceTexture` that the command begins copying data from.

Assign `0` to each dimension that’s not relevant to `sourceTexture`. For example:

- If the source texture is a 2D texture, set the origin’s z property to `0`.

- If the source texture is a 1D texture, set the origin’s y and z properties to `0`.

`sourceSize`  

An MTLSize instance, which can represent a 3D region, that instructs the command how many pixels to copy from `sourceTexture`, starting at `sourceOrigin`.

Assign `1` to each dimension that’s not relevant to `sourceTexture`. For example:

- If the source texture is a 2D texture, set the size’s depth property to `1`.

- If the source texture is a 1D texture, set the size’s height and depth properties to `1`.

If `sourceTexture` uses a compressed pixel format, set `sourceSize` to a multiple of the pixel format’s block size. If the block extends outside the bounds of the texture, clamp `sourceSize` to the edge of the texture.

`destinationTexture`  

A texture the command copies data to that has the following configuration:

- The isFramebufferOnly property value is false.

- The pixel format is the same as `sourceTexture`.

- The sample count is the same as `sourceTexture`.

For a texture that uses a compressed pixel format, align the copy region (`destinationOrigin`) to the pixel format’s block size.

`destinationSlice`  

A slice within `destinationTexture`.

`destinationLevel`  

A mipmap level within `destinationTexture`.

`destinationOrigin`  

A location within `destinationTexture` that the command begins copying data to.

Assign `0` to each dimension that’s not relevant to `destinationTexture`. For example:

- If the destination texture is a 2D texture, set the origin’s z property to `0`.

- If the destination texture is a 1D texture, set the origin’s y and z properties to `0`.

## Mentioned in 

Copying Data to a Private Resource

## Discussion

For textures that use a PVRTC pixel format, you can use this method to copy the entire texture, but not a subregion of the texture.

Important

Copying data to overlapping regions within the same texture may result in unexpected behavior.

## See Also

### Copying Texture Data to Another Texture

func copy(from: any MTLTexture, to: any MTLTexture)

Encodes a command that copies data from one texture to another.

**Required**

func copy(from: any MTLTexture, sourceSlice: Int, sourceLevel: Int, to: any MTLTexture, destinationSlice: Int, destinationLevel: Int, sliceCount: Int, levelCount: Int)

Encodes a command that copies slices of a texture to another texture’s slices.

**Required**

