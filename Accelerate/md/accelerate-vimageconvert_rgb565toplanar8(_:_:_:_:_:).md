

- Accelerate
-  vImageConvert_RGB565toPlanar8(\_:\_:\_:\_:\_:) 

Function

# vImageConvert_RGB565toPlanar8(\_:\_:\_:\_:\_:)

Deinterleaves an RGB565 3-channel interleaved buffer into three 8-bit planar buffers.

iOS 5.0+iPadOS 5.0+Mac Catalyst 13.1+macOS 10.4+tvOS 5.0+visionOS 1.0+watchOS 1.0+

``` source
func vImageConvert_RGB565toPlanar8(
    _ src: UnsafePointer,
    _ destR: UnsafePointer,
    _ destG: UnsafePointer,
    _ destB: UnsafePointer,
    _ flags: vImage_Flags
) -> vImage_Error
```

## Parameters 

`src`  

The source vImage buffer.

`destR`  

A pointer to the red destination vImage buffer structure. You’re responsible for filling out the height, width, and rowBytes fields of this structure, and for allocating a data buffer of the appropriate size. On return, the data buffer this structure points to contains the red destination image data. When you no longer need the data buffer, deallocate the memory to prevent memory leaks.

`destG`  

A pointer to the green destination vImage buffer structure. You’re responsible for filling out the height, width, and rowBytes fields of this structure, and for allocating a data buffer of the appropriate size. On return, the data buffer this structure points to contains the green destination image data. When you no longer need the data buffer, deallocate the memory to prevent memory leaks.

`destB`  

A pointer to the blue destination vImage buffer structure. You’re responsible for filling out the height, width, and rowBytes fields of this structure, and for allocating a data buffer of the appropriate size. On return, the data buffer this structure points to contains the blue destination image data. When you no longer need the data buffer, deallocate the memory to prevent memory leaks.

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

