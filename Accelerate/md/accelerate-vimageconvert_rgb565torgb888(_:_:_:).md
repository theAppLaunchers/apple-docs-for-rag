

- Accelerate
-  vImageConvert_RGB565toRGB888(\_:\_:\_:) 

Function

# vImageConvert_RGB565toRGB888(\_:\_:\_:)

Converts an RGB565 3-channel interleaved buffer to an 8-bit-per-channel, 3-channel interleaved buffer.

iOS 8.0+iPadOS 8.0+Mac Catalyst 13.1+macOS 10.10+tvOS 8.0+visionOS 1.0+watchOS 1.0+

``` source
func vImageConvert_RGB565toRGB888(
    _ src: UnsafePointer,
    _ dest: UnsafePointer,
    _ flags: vImage_Flags
) -> vImage_Error
```

## Parameters 

`src`  

The source vImage buffer.

`dest`  

A pointer to the destination vImage buffer structure. You’re responsible for filling out the height, width, and rowBytes fields of this structure, and for allocating a data buffer of the appropriate size. On return, the data buffer this structure points to contains the destination image data. When you no longer need the data buffer, deallocate the memory to prevent memory leaks.

`flags`  

The options to use when performing the operation. If your code implements its own tiling or its own multithreading, pass kvImageDoNotTile; otherwise, pass kvImageNoFlags.

## Return Value

kvImageNoError; otherwise, one of the error codes in Data Types and Constants.

## Discussion

The function uses the following calculation to perform the conversion:

```
 Pixel8 red   = (5bitRedChannel   * 255 + 15) / 31;
 Pixel8 green = (6bitGreenChannel * 255 + 31) / 63;
 Pixel8 blue  = (5bitBlueChannel  * 255 + 15) / 31;
```

