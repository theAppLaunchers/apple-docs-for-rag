

- Compression
-  compression_decode_buffer(\_:\_:\_:\_:\_:\_:) 

Function

# compression_decode_buffer(\_:\_:\_:\_:\_:\_:)

Decompresses the contents of a source buffer into a destination buffer.

iOS 9.0+iPadOS 9.0+Mac Catalyst 13.1+macOS 10.11+tvOS 9.0+visionOS 1.0+watchOS 2.0+

``` source
func compression_decode_buffer(
    _ dst_buffer: UnsafeMutablePointer,
    _ dst_size: Int,
    _ src_buffer: UnsafePointer,
    _ src_size: Int,
    _ scratch_buffer: UnsafeMutableRawPointer?,
    _ algorithm: compression_algorithm
) -> Int
```

## Parameters 

`dst_buffer`  

Pointer to the buffer that receives the decompressed data.

`dst_size`  

Size of the destination buffer in bytes.

`src_buffer`  

Pointer to a buffer containing all of the compressed source data.

`src_size`  

Size of the data in the source buffer in bytes.

`scratch_buffer`  

If `scratch_buffer` is not `nil`, this parameter is a pointer to a buffer that the function uses for scratch purposes. The size of this buffer must be at least the size returned by a previous call to compression_decode_scratch_buffer_size(_:).

If `scratch_buffer` is `nil`, the function creates and manages its own scratch space, but with a possible performance hit.

`algorithm`  

Set to the desired algorithm: COMPRESSION_LZ4, COMPRESSION_ZLIB, COMPRESSION_LZMA, or COMPRESSION_LZFSE.

## Return Value

The number of bytes written to the destination buffer after decompressing the input. If there is not enough space in the destination buffer to hold the entire decompressed output, the function writes the first `dst_size` bytes to the buffer and returns `dst_size`. Note that this behavior differs from that of compression_encode_buffer(_:_:_:_:_:_:).

## Discussion

The function writes the decompressed data to `dst_buffer`.

## See Also

### Single-step compression

Compressing and decompressing data with buffer compression

Compress a string, write it to the file system, and decompress the same file using buffer compression.

func compression_encode_scratch_buffer_size(compression_algorithm) -> Int

Returns the required compression scratch buffer size for the selected algorithm.

func compression_encode_buffer(UnsafeMutablePointer&lt;UInt8>, Int, UnsafePointer&lt;UInt8>, Int, UnsafeMutableRawPointer?, compression_algorithm) -> Int

Compresses the contents of a source buffer into a destination buffer.

func compression_decode_scratch_buffer_size(compression_algorithm) -> Int

Returns the required decompression scratch buffer size for the selected algorithm.

struct compression_algorithm

A structure for values that represent compression algorithms.

