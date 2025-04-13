

- Accelerate
-  vImageConvert_AnyToAny(\_:\_:\_:\_:\_:) 

Function

# vImageConvert_AnyToAny(\_:\_:\_:\_:\_:)

Converts the pixels in a vImage buffer to another format, using the specified converter.

iOS 7.0+iPadOS 7.0+Mac Catalyst 13.1+macOS 10.9+tvOS 7.0+visionOS 1.0+watchOS 1.0+

``` source
func vImageConvert_AnyToAny(
    _ converter: vImageConverter,
    _ srcs: UnsafePointer,
    _ dests: UnsafePointer,
    _ tempBuffer: UnsafeMutableRawPointer!,
    _ flags: vImage_Flags
) -> vImage_Error
```

## Parameters 

`converter`  

A valid vImageConverter instance indicating the conversion to perform. You can use the same converter concurrently in multiple threads. To create a converter, you can use vImageConverter_CreateWithCGImageFormat(_:_:_:_:_:), vImageConverter_CreateWithColorSyncCodeFragment(_:_:_:_:_:_:), vImageConverter_CreateForCGToCVImageFormat(_:_:_:_:_:), or vImageConverter_CreateForCVToCGImageFormat(_:_:_:_:_:).

`srcs`  

A pointer to an array of vImage buffer structs that describe the color planes that make up the input image. For the order and number of input buffers, see the description of the function that created the vImageConverter instance. You can also determine the order manually using vImageConverter_GetSourceBufferOrder(_:).

`dests`  

A pointer to an array of vImage buffer structs that describe the color planes that make up the result image. For the order and number of input buffers, see the description of the function that created the vImageConverter instance. You can also determine the order manually using vImageConverter_GetDestinationBufferOrder(_:). The destination buffer may only alias the `srcs` buffers if vImageConverter_MustOperateOutOfPlace(_:_:_:_:) returns 0 and the respective scanlines of the aliasing buffers start at the same address.

`tempBuffer`  

If this value isn’t null, the memory that `tempBuffer` points to is used as scratch space by the function. You can determine the buffer size by passing kvImageGetTempBufferSize to the flags parameter. If null is passed here and a temporary buffer is needed, the function allocates one on the heap and frees it before returning. The function may run more slowly, because of both the allocation cost and the cost of virtual memory faults to zero-fill pages as they are used. `nil` is the correct option when the function is used infrequently or convenience is valued.

`flags`  

The options to use when performing this operation. The following flags are supported:

| kvImagePrintDiagnosticsToConsole | Prints a debug message if the operation fails. |
|----|----|
| kvImageGetTempBufferSize | No image conversion work is done. If the value returned by the function is less than 0, it represents an error code. A value of 0 or greater represents the size of `tempBuffer` to be passed into the function. |
| kvImageDoNotTile | Disables internal multithreading. Pass this flag if you’re doing your own threading and think it will conflict with vImage’s attempts to do the same. |
| kvImageNoFlags | Default behavior. |

## Return Value

kvImageNoError; otherwise, one of the error codes described in Data Types and Constants.

## Mentioned in 

Building a basic image conversion workflow

## Discussion

With an appropriately configured vImage converter, convert the image channels found in `srcs` to the image channels found in `dests`. Whenever possible, conversion passes are vectorized and multithreaded to reduce the time and energy cost of the function.

Use vImageConverter_MustOperateOutOfPlace(_:_:_:_:) to determine whether a particular conversion can operate in place. For an in-place conversion to work, you must ensure that `srcs[i].data = dests[i].data` and `srcs[i].rowBytes = dests[i].rowBytes`.

All scanlines must start at a byte-aligned address. Some formats have 1, 2, 4, or 12 bits per channel/pixel and might not start at a byte-aligned address. A single byte can’t span multiple rows of data.

Some formats, particularly YUV422 and YUV420, and those with a pixel size that’s not evenly divisible by 8 bits, operate in chunks containing multiple pixels. For example, a YCbCr422 chunk may have `{Y0, Cb, Y1, Cr}` in the chunk. The chunk contains two pixels, each with an independent Y (luminance) component, but shared chrominance. Even though the chunk width is two, it’s still possible for an image to have a width that’s not divisible by two. This means that some part of the chunk on the rightmost edge of the scanline must refer to a nonexistent pixel.

When reading incomplete chunks, vImage touches only the unused parts of the chunk when it knows it to be safe to do so. When writing incomplete chunks, vImage copies the rightmost valid pixel color into the unused part of the chunk. Thus, on reading, the entire chunk doesn’t have to be there, but on writing, it does. Conventions vary among chunk-using imaging pipelines, and this conservative approach should interoperate with most. However, be careful when writing to chunk-based formats (not to be confused with chunky formats, which merely have several channels interleaved) to make sure that the buffer is large enough to tolerate the write policy. If you’re tiling chunk-based data, be careful not to run tile boundaries through the middle of a chunk. Chunks are assumed to be indivisible.

## See Also

### Performing a conversion

vImage Buffer Type Codes

Constants that specify the contents of vImage buffers.

