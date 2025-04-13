

- Accelerate
-  vImageConvert_420Yp8_CbCr8ToARGB8888(\_:\_:\_:\_:\_:\_:\_:) 

Function

# vImageConvert_420Yp8_CbCr8ToARGB8888(\_:\_:\_:\_:\_:\_:\_:)

Converts a planar Yp buffer and a 2-channel CbCr buffer to an 8-bit-per-channel, 4-channel ARGB buffer.

iOS 8.0+iPadOS 8.0+Mac Catalyst 13.1+macOS 10.10+tvOS 8.0+visionOS 1.0+watchOS 1.0+

``` source
func vImageConvert_420Yp8_CbCr8ToARGB8888(
    _ srcYp: UnsafePointer,
    _ srcCbCr: UnsafePointer,
    _ dest: UnsafePointer,
    _ info: UnsafePointer,
    _ permuteMap: UnsafePointer!,
    _ alpha: UInt8,
    _ flags: vImage_Flags
) -> vImage_Error
```

## Parameters 

`srcYp`  

The source vImage buffer that contains the Yp channel.

`srcCbCr`  

The source vImage buffer that contains the CbCr channels.

`dest`  

A pointer to the destination vImage buffer structure. You’re responsible for filling out the height, width, and rowBytes fields of this structure, and for allocating a data buffer of the appropriate size. On return, the data buffer this structure points to contains the destination image data. When you no longer need the data buffer, deallocate the memory to prevent memory leaks.

`info`  

A vImage_YpCbCrToARGB structure that describes the conversion matrix, the range of the input and output pixels from the matrix, and clamping information.

`permuteMap`  

An array of four 8-bit integers with the values `0`, `1`, `2`, and 3, in some order. Each value specifies the channel from the source image that the function copies to the destination channel at the corresponding index.

`alpha`  

The constant destination alpha value.

`flags`  

The options to use when performing the operation. If your code implements its own tiling or its own multithreading, pass kvImageDoNotTile; otherwise, pass kvImageNoFlags.

## Return Value

kvImageNoError; otherwise, one of the error codes in Data Types and Constants.

## See Also

### Converting from 4:2:0

func vImageConvert_420Yp8_Cb8_Cr8ToARGB8888(UnsafePointer&lt;vImage_Buffer>, UnsafePointer&lt;vImage_Buffer>, UnsafePointer&lt;vImage_Buffer>, UnsafePointer&lt;vImage_Buffer>, UnsafePointer&lt;vImage_YpCbCrToARGB>, UnsafePointer&lt;UInt8>!, UInt8, vImage_Flags) -> vImage_Error

Converts planar Yp, Cb, and Cr buffers to an 8-bit-per-channel, 4-channel ARGB buffer.

