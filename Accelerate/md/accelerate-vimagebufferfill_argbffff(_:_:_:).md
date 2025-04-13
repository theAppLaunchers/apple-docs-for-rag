

- Accelerate
-  vImageBufferFill_ARGBFFFF(\_:\_:\_:) 

Function

# vImageBufferFill_ARGBFFFF(\_:\_:\_:)

Fills a floating-point 32-bit-per-channel, 4-channel interleaved buffer with a specified color.

iOS 5.0+iPadOS 5.0+Mac Catalyst 13.1+macOS 10.4+tvOS 5.0+visionOS 1.0+watchOS 1.0+

``` source
func vImageBufferFill_ARGBFFFF(
    _ dest: UnsafePointer,
    _ color: UnsafePointer,
    _ flags: vImage_Flags
) -> vImage_Error
```

## Parameters 

`dest`  

A pointer to the destination vImage buffer structure. You’re responsible for filling out the height, width, and rowBytes fields of this structure, and for allocating a data buffer of the appropriate size. On return, the data buffer this structure points to contains the destination image data. When you no longer need the data buffer, deallocate the memory to prevent memory leaks.

`color`  

The fill color.

`flags`  

The options to use when performing the operation. If your code implements its own tiling or its own multithreading, pass kvImageDoNotTile; otherwise, pass kvImageNoFlags.

## Return Value

kvImageNoError; otherwise, one of the error codes in Data Types and Constants.

## Discussion

The following code fills the buffer with the specified color:

```
let pixelBuffer = vImage.PixelBuffer(
    size: .init(width: 1, height: 2))

let fillColor: [Pixel_F] = [64, 127, 192, 255]

pixelBuffer.withUnsafePointerToVImageBuffer { buf in
    _ = vImageBufferFill_ARGBFFFF(buf,
                                 fillColor,
                                 vImage_Flags(kvImageNoFlags))
}

print(pixelBuffer.array)
// Prints:
//      "[64.0, 127.0, 192.0, 255.0,
//        64.0, 127.0, 192.0, 255.0]"
```

## See Also

### Filling buffers

func vImageBufferFill_CbCr8(UnsafePointer&lt;vImage_Buffer>, UnsafePointer&lt;UInt8>, vImage_Flags) -> vImage_Error

Fills an 8-bit-per-channel, 2-channel interleaved buffer with a specified color.

func vImageBufferFill_CbCr16U(UnsafePointer&lt;vImage_Buffer>, UnsafePointer&lt;UInt16>, vImage_Flags) -> vImage_Error

Fills an unsigned 16-bit-per-channel, 2-channel interleaved buffer with a specified color.

func vImageBufferFill_CbCr16S(UnsafePointer&lt;vImage_Buffer>, UnsafePointer&lt;Int16>, vImage_Flags) -> vImage_Error

func vImageBufferFill_ARGB8888(UnsafePointer&lt;vImage_Buffer>, UnsafePointer&lt;UInt8>, vImage_Flags) -> vImage_Error

Fills an 8-bit-per-channel, 4-channel interleaved buffer with a specified color.

func vImageBufferFill_ARGB16U(UnsafePointer&lt;vImage_Buffer>, UnsafePointer&lt;UInt16>, vImage_Flags) -> vImage_Error

Fills an unsigned 16-bit-per-channel, 4-channel interleaved buffer with a specified color.

func vImageBufferFill_ARGB16S(UnsafePointer&lt;vImage_Buffer>, UnsafePointer&lt;Int16>, vImage_Flags) -> vImage_Error

Fills a signed 16-bit-per-channel, 4-channel interleaved buffer with a specified color.

func vImageBufferFill_ARGB16F(UnsafePointer&lt;vImage_Buffer>, UnsafePointer&lt;UInt16>, vImage_Flags) -> vImage_Error

Fills a floating-point 16-bit-per-channel, 4-channel interleaved buffer with a specified color.

