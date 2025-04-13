

- Accelerate
-  vImageRotate90_Planar16U(\_:\_:\_:\_:\_:) 

Function

# vImageRotate90_Planar16U(\_:\_:\_:\_:\_:)

Rotates an unsigned 16-bit planar image by a multiple of 90°.

iOS 6.0+iPadOS 6.0+Mac Catalyst 13.1+macOS 10.9+tvOS 6.0+visionOS 1.0+watchOS 1.0+

``` source
func vImageRotate90_Planar16U(
    _ src: UnsafePointer,
    _ dest: UnsafePointer,
    _ rotationConstant: UInt8,
    _ backColor: Pixel_16U,
    _ flags: vImage_Flags
) -> vImage_Error
```

## Parameters 

`src`  

A pointer to a vImage buffer structure that contains the source image.

`dest`  

A pointer to the destination vImage buffer structure. You’re responsible for filling out the `height`, `width`, and `rowBytes` fields of this structure and for allocating a data buffer of the appropriate size. On return, the data buffer this structure points to contains the destination image data. When you no longer need the data buffer, deallocate the memory to prevent memory leaks.

`rotationConstant`  

A constant that specifies the rotation angle as a multiple of 90°. See Rotation constants for the full list of supported rotation constants.

`backColor`  

A background color. If you set the `kvImageBackgroundColorFill` flag, pass a pixel value.

`flags`  

The options to use when performing the operation. If your code implements its own tiling or its own multithreading, pass kvImageDoNotTile; otherwise, pass kvImageNoFlags.

## Return Value

kvImageNoError; otherwise, one of the error codes from Error codes.

## Discussion

This function maps the center point of the source image to the center point of the destination image. It doesn’t scale or resample; instead, the function copies unchanged individual pixels to new locations.

Depending on the relative sizes of the source image and the destination buffer, the function may clip parts of the source image. Areas outside the source image might appear in the destination image if you don’t pass a background color to the function.

The 90° and 270° rotations don’t rotate around the true center of the image if either of the following is true:

- The parities of the source height and the destination width don’t match. For example, the source height is odd and the destination width is even.

- The parities of the source width and the destination height don’t match. For example, the source width is odd and the destination height is even.

The 0° and 180° rotations don’t rotate around the true center of the image if either of the following is true:

- The parities of the source height and the destination height don’t match. For example, the source height is odd and the destination height is even.

- The parities of the source width and the destination width don’t match. For example, the source width is odd and the destination width is even.

To overcome this limitation, use the high-level rotation functions — for example, vImageRotate90_ARGB16U(_:_:_:_:_:).

## See Also

### Related Documentation

Applying geometric transforms to images

Reflect, shear, rotate, and scale image buffers using vImage.

### Rotating 16-bit-per-channel buffers by multiples of 90°

func vImageRotate90_Planar16F(UnsafePointer&lt;vImage_Buffer>, UnsafePointer&lt;vImage_Buffer>, UInt8, Pixel_16F, vImage_Flags) -> vImage_Error

Rotates a floating-point 16-bit planar image by a multiple of 90°.

func vImageRotate90_CbCr16F(UnsafePointer&lt;vImage_Buffer>, UnsafePointer&lt;vImage_Buffer>, UInt8, UnsafePointer&lt;UInt16>!, vImage_Flags) -> vImage_Error

Rotates a floating-point 16-bit-per-channel, 2-channel interleaved image by a multiple of 90°.

func vImageRotate90_ARGB16U(UnsafePointer&lt;vImage_Buffer>, UnsafePointer&lt;vImage_Buffer>, UInt8, UnsafePointer&lt;UInt16>, vImage_Flags) -> vImage_Error

Rotates an unsigned 16-bit-per-channel, 4-channel interleaved image by a multiple of 90°.

func vImageRotate90_ARGB16S(UnsafePointer&lt;vImage_Buffer>, UnsafePointer&lt;vImage_Buffer>, UInt8, UnsafePointer&lt;Int16>, vImage_Flags) -> vImage_Error

Rotates a signed 16-bit-per-channel, 4-channel interleaved image by a multiple of 90°.

func vImageRotate90_ARGB16F(UnsafePointer&lt;vImage_Buffer>, UnsafePointer&lt;vImage_Buffer>, UInt8, UnsafePointer&lt;UInt16>!, vImage_Flags) -> vImage_Error

Rotates a floating-point 16-bit-per-channel, 4-channel interleaved image by a multiple of 90°.

