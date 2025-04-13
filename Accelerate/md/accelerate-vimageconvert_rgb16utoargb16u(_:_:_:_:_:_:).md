

- Accelerate
-  vImageConvert_RGB16UtoARGB16U(\_:\_:\_:\_:\_:\_:) 

Function

# vImageConvert_RGB16UtoARGB16U(\_:\_:\_:\_:\_:\_:)

Combines an unsigned 16-bit-per-channel, 3-channel RGB buffer and either an unsigned 16-bit alpha buffer or constant alpha value to produce an ARGB result.

iOS 7.0+iPadOS 7.0+Mac Catalyst 13.1+macOS 10.9+tvOS 7.0+visionOS 1.0+watchOS 1.0+

``` source
func vImageConvert_RGB16UtoARGB16U(
    _ rgbSrc: UnsafePointer,
    _ aSrc: UnsafePointer!,
    _ alpha: Pixel_16U,
    _ argbDest: UnsafePointer,
    _ premultiply: Bool,
    _ flags: vImage_Flags
) -> vImage_Error
```

## Parameters 

`rgbSrc`  

The source vImage buffer that contains the red, green, and blue channels.

`aSrc`  

The source vImage buffer that contains the alpha channel. Set this value to `nil` to specify that the function sets the destination alpha as the constant destination alpha value.

`alpha`  

The constant destination alpha value. The function ignores this paramater if the `aSrc` parameter isn’t `nil`.

`argbDest`  

A pointer to the destination vImage buffer structure. You’re responsible for filling out the height, width, and rowBytes fields of this structure, and for allocating a data buffer of the appropriate size. On return, the data buffer this structure points to contains the destination image data. When you no longer need the data buffer, deallocate the memory to prevent memory leaks.

`premultiply`  

A Boolean value that specifes whether the function premultiplies the color channels by the alpha channel.

`flags`  

The options to use when performing the operation. If your code implements its own tiling or its own multithreading, pass kvImageDoNotTile; otherwise, pass kvImageNoFlags.

## Return Value

kvImageNoError; otherwise, one of the error codes in Data Types and Constants.

## Discussion

The function uses the following calculation to perform the conversion:

```
if (aSrc != NULL)
 {
    if (premultiply)
    {
        r = (aSrc[i] * rgb[i*3+0] + 32767) / 65535
        g = (aSrc[i] * rgb[i*3+1] + 32767) / 65535
        b = (aSrc[i] * rgb[i*3+2] + 32767) / 65535

        argbDest[i*4+0] = aSrc[i];
        argbDest[i*4+1] = r;
        argbDest[i*4+2] = g;
        argbDest[i*4+3] = b;
    }
    else
    {
        argbDest[i*4+0] = aSrc[i];
        argbDest[i*4+1] = rgb[i*3+0];
        argbDest[i*4+2] = rgb[i*3+1];
        argbDest[i*4+3] = rgb[i*3+2];
    }
 }
 else
 {
    if (premultiply)
    {
        r = (alpha * rgb[i*3+0] + 32767) / 65535
        g = (alpha * rgb[i*3+1] + 32767) / 65535
        b = (alpha * rgb[i*3+2] + 32767) / 65535

        argbDest[i*4+0] = alpha;
        argbDest[i*4+1] = r;
        argbDest[i*4+2] = g;
        argbDest[i*4+3] = b;
    }
    else
    {
        argbDest[i*4+0] = alpha;
        argbDest[i*4+1] = rgb[i*3+0];
        argbDest[i*4+2] = rgb[i*3+1];
        argbDest[i*4+3] = rgb[i*3+2];
    }
 }
```

This function doesn’t operate in place.

## See Also

### Conversion from unsigned 16-bit-per-channel, 3-channel interleaved buffers

func vImageConvert_RGB16UToARGB8888(UnsafePointer&lt;vImage_Buffer>, UnsafePointer&lt;vImage_Buffer>, UnsafePointer&lt;UInt8>, UInt8, UnsafePointer&lt;UInt8>, vImage_Flags) -> vImage_Error

Converts an unsigned 16-bit-per-channel, 3-channel interleaved buffer to an 8-bit-per-channel, 4-channel interleaved buffer using permutation.

func vImageConvert_RGB16UtoBGRA16U(UnsafePointer&lt;vImage_Buffer>, UnsafePointer&lt;vImage_Buffer>!, Pixel_16U, UnsafePointer&lt;vImage_Buffer>, Bool, vImage_Flags) -> vImage_Error

Combines an unsigned 16-bit-per-channel, 3-channel RGB buffer and either an unsigned 16-bit alpha buffer or constant alpha value to produce a BGRA result.

func vImageConvert_RGB16UtoRGBA16U(UnsafePointer&lt;vImage_Buffer>, UnsafePointer&lt;vImage_Buffer>!, Pixel_16U, UnsafePointer&lt;vImage_Buffer>, Bool, vImage_Flags) -> vImage_Error

Combines an unsigned 16-bit-per-channel, 3-channel RGB buffer and either an unsigned 16-bit alpha buffer or constant alpha value to produce an RGBA result.

