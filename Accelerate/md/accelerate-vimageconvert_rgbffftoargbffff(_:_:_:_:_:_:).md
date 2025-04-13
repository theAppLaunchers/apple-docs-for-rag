

- Accelerate
-  vImageConvert_RGBFFFtoARGBFFFF(\_:\_:\_:\_:\_:\_:) 

Function

# vImageConvert_RGBFFFtoARGBFFFF(\_:\_:\_:\_:\_:\_:)

Combines a floating-point 32-bit-per-channel, 3-channel RGB buffer and either an 32-bit alpha buffer or constant alpha value to produce an ARGB result.

iOS 7.0+iPadOS 7.0+Mac Catalyst 13.1+macOS 10.9+tvOS 7.0+visionOS 1.0+watchOS 1.0+

``` source
func vImageConvert_RGBFFFtoARGBFFFF(
    _: UnsafePointer,
    _: UnsafePointer!,
    _: Pixel_F,
    _: UnsafePointer,
    _: Bool,
    _ flags: vImage_Flags
) -> vImage_Error
```

## Return Value

kvImageNoError; otherwise, one of the error codes in Data Types and Constants.

## Discussion

### Parameters

rgbSrc  
The source vImage buffer that contains the red, green, and blue channels.

aSrc  
The source vImage buffer that contains the alpha channel. Set this value to `nil` to specify that the function sets the destination alpha as the constant destination alpha value.

alpha  
The constant destination alpha value. The function ignores this paramater if the `aSrc` parameter isn’t `nil`.

argbDest  
A pointer to the destination vImage buffer structure. You’re responsible for filling out the height, width, and rowBytes fields of this structure, and for allocating a data buffer of the appropriate size. On return, the data buffer this structure points to contains the destination image data. When you no longer need the data buffer, deallocate the memory to prevent memory leaks.

premultiply  
A Boolean value that specifes whether the function premultiplies the color channels by the alpha channel.

flags  
The options to use when performing the operation. If your code implements its own tiling or its own multithreading, pass kvImageDoNotTile; otherwise, pass kvImageNoFlags.

If you specify `premultiply` as `true`, the function uses the following calculation to perform the conversion:

```
 r = (a * r)
 g = (a * g)
 b = (a * b)
```

## See Also

### Conversion from 32-bit-per-channel, 3-channel interleaved buffers

func vImageConvert_RGBFFFtoBGRAFFFF(UnsafePointer&lt;vImage_Buffer>, UnsafePointer&lt;vImage_Buffer>!, Pixel_F, UnsafePointer&lt;vImage_Buffer>, Bool, vImage_Flags) -> vImage_Error

Combines a floating-point 32-bit-per-channel, 3-channel RGB buffer and either an 32-bit alpha buffer or constant alpha value to produce a BGRA result.

func vImageConvert_RGBFFFtoRGBAFFFF(UnsafePointer&lt;vImage_Buffer>, UnsafePointer&lt;vImage_Buffer>!, Pixel_F, UnsafePointer&lt;vImage_Buffer>, Bool, vImage_Flags) -> vImage_Error

Combines a floating-point 32-bit-per-channel, 3-channel RGB buffer and either an 32-bit alpha buffer or constant alpha value to produce an RGBA result.

