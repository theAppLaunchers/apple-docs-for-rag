

- Accelerate
-  vImageConvert_Planar8To16U(\_:\_:\_:) 

Function

# vImageConvert_Planar8To16U(\_:\_:\_:)

Converts an 8-bit planar buffer to an unsigned 16-bit planar buffer.

iOS 5.0+iPadOS 5.0+Mac Catalyst 13.1+macOS 10.4+tvOS 5.0+visionOS 1.0+watchOS 1.0+

``` source
func vImageConvert_Planar8To16U(
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
uint16_t result = (srcPixel * 65535 + 127 ) / 255
```

## See Also

### Converting from 8-bit buffers

func vImageConvert_Planar8toPlanar1(UnsafePointer&lt;vImage_Buffer>, UnsafePointer&lt;vImage_Buffer>, UnsafeMutableRawPointer!, Int32, vImage_Flags) -> vImage_Error

Converts an 8-bit planar buffer to a 1-bit planar buffer.

func vImageConvert_Planar8toPlanar2(UnsafePointer&lt;vImage_Buffer>, UnsafePointer&lt;vImage_Buffer>, UnsafeMutableRawPointer!, Int32, vImage_Flags) -> vImage_Error

Converts an 8-bit planar buffer to a 2-bit planar buffer.

func vImageConvert_Planar8toPlanar4(UnsafePointer&lt;vImage_Buffer>, UnsafePointer&lt;vImage_Buffer>, UnsafeMutableRawPointer!, Int32, vImage_Flags) -> vImage_Error

Converts an 8-bit planar buffer to a 4-bit planar buffer.

func vImageConvert_Planar8toIndexed1(UnsafePointer&lt;vImage_Buffer>, UnsafePointer&lt;vImage_Buffer>, UnsafeMutableRawPointer!, UnsafeMutablePointer&lt;Pixel_8>, Int32, vImage_Flags) -> vImage_Error

Converts an 8-bit planar buffer to an indexed 1-bit planar buffer.

func vImageConvert_Planar8toIndexed2(UnsafePointer&lt;vImage_Buffer>, UnsafePointer&lt;vImage_Buffer>, UnsafeMutableRawPointer!, UnsafeMutablePointer&lt;Pixel_8>, Int32, vImage_Flags) -> vImage_Error

Converts an 8-bit planar buffer to an indexed 2-bit planar buffer.

func vImageConvert_Planar8toIndexed4(UnsafePointer&lt;vImage_Buffer>, UnsafePointer&lt;vImage_Buffer>, UnsafeMutableRawPointer!, UnsafeMutablePointer&lt;Pixel_8>, Int32, vImage_Flags) -> vImage_Error

Converts an 8-bit planar buffer to an indexed 4-bit planar buffer.

