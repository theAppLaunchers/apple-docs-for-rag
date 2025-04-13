

- Accelerate
-  vImageConvert_PlanarToChunkyF(\_:\_:\_:\_:\_:\_:\_:\_:) 

Function

# vImageConvert_PlanarToChunkyF(\_:\_:\_:\_:\_:\_:\_:\_:)

Interleaves the specifed number of floating-point 32-bit planar buffers into a floating-point 32 -bit-per-channel interleaved buffer.

iOS 5.0+iPadOS 5.0+Mac Catalyst 13.1+macOS 10.3+tvOS 5.0+visionOS 1.0+watchOS 1.0+

``` source
func vImageConvert_PlanarToChunkyF(
    _ srcPlanarBuffers: UnsafeMutablePointer?>,
    _ destChannels: UnsafeMutablePointer,
    _ channelCount: UInt32,
    _ destStrideBytes: Int,
    _ destWidth: vImagePixelCount,
    _ destHeight: vImagePixelCount,
    _ destRowBytes: Int,
    _ flags: vImage_Flags
) -> vImage_Error
```

## Parameters 

`srcPlanarBuffers`  

An array that contains `channelCount` source planar vImage buffers. Each source buffer must be the same height and width, but they may have different rowBytes values.

`destChannels`  

An array that contains pointers to the start of each channel in the destination buffer.

`channelCount`  

The number of channels in the destination image.

`destStrideBytes`  

The number of bytes between consecutive pixels in a channel in the same row.

`destWidth`  

The width, in pixels, of the destination channels and the source planar buffers.

`destHeight`  

The height, in pixels, of the destination channels and the source planar buffers.

`destRowBytes`  

The distance, in bytes, between the corresponding pixels in consecutive rows in the destination buffer, including any unused space between them.

`flags`  

The options to use when performing the operation. If your code implements its own tiling or its own multithreading, pass kvImageDoNotTile; otherwise, pass kvImageNoFlags.

## Return Value

kvImageNoError; otherwise, one of the error codes in Data Types and Constants.

## Discussion

Use this function to interleave formats that either aren’t supported by the vImage library or are only known at runtime.

The following code interleaves two 4 x 1 planar buffers into a 4 x 1 interleaved 2-channel buffer:

```
let width = 4
let height = 1
let size = vImage.Size(width: width,
                       height: height)

let cbBuffer = vImage.PixelBuffer(pixelValues: [10, 11, 12, 13],
                                  size: size,
                                  pixelFormat: vImage.PlanarF.self)

let crBuffer = vImage.PixelBuffer(pixelValues: [20, 21, 22, 23],
                                  size: size,
                                  pixelFormat: vImage.PlanarF.self)

let cbCrBuffer = vImage.PixelBuffer(size: size,
                                    pixelFormat: vImage.InterleavedFx2.self)

cbBuffer.withUnsafePointerToVImageBuffer { cb in
    crBuffer.withUnsafePointerToVImageBuffer { cr in
        cbCrBuffer.withUnsafeVImageBuffer { cbcr in

            var srcPlanarBuffers = [Optional(cb), Optional(cr)]
            var destChannels = [
                cbcr.data,
                cbcr.data.advanced(by: MemoryLayout.stride)
            ]

            let channelCount = 2

            _ = vImageConvert_PlanarToChunkyF(
                &srcPlanarBuffers,
                &destChannels,
                UInt32(channelCount),
                MemoryLayout.stride * channelCount,
                vImagePixelCount(width),
                vImagePixelCount(height),
                cbcr.rowBytes,
                vImage_Flags(kvImageNoFlags))

        }
    }
}

// Prints "[10.0, 20.0,   11.0, 21.0,   12.0, 22.0,   13.0, 23.0]".
print(cbCrBuffer.array)
```

