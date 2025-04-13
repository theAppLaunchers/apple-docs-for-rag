

- Core Media
-  CMBlockBufferCreateContiguous(allocator:sourceBuffer:blockAllocator:customBlockSource:offsetToData:dataLength:flags:blockBufferOut:) 

Function

# CMBlockBufferCreateContiguous(allocator:sourceBuffer:blockAllocator:customBlockSource:offsetToData:dataLength:flags:blockBufferOut:)

Creates a block buffer that contains a contiguous copy of, or reference to, the data specified by the parameters.

iOS 4.0+iPadOS 4.0+Mac Catalyst 13.1+macOS 10.7+tvOS 9.0+visionOS 1.0+watchOS 6.0+

``` source
func CMBlockBufferCreateContiguous(
    allocator structureAllocator: CFAllocator?,
    sourceBuffer: CMBlockBuffer,
    blockAllocator: CFAllocator?,
    customBlockSource: UnsafePointer?,
    offsetToData: Int,
    dataLength: Int,
    flags: CMBlockBufferFlags,
    blockBufferOut: UnsafeMutablePointer
) -> OSStatus
```

## Parameters 

`structureAllocator`  

Allocator to use for allocating the `CMBlockBuffer` object. `NULL` will cause the default allocator to be used.

`sourceBuffer`  

`CMBlockBuffer` from which data will be copied or referenced. Must not be `NULL` or empty.

`blockAllocator`  

Allocator to be used for allocating the memory block if a contiguous copy of the data is to be made. Passing `NULL` will cause the default allocator (as set at the time of the call) to be used.

`customBlockSource`  

If non-`NULL`, it will be used for the allocation and freeing of the memory block (the `blockAllocator` parameter is ignored). If provided, and the parameter `kCMBlockBufferAlwaysCopyDataFlag` is set, `customBlockSource’s` `AllocateBlock()` routine must be non-`NULL`. Allocate will be called once, if successful, when the memory block is allocated. FreeBlock will be called once when the `CMBlockBuffer` is disposed.

`offsetToData`  

Offset within the source `CMBlockBuffer` at which the new `CMBlockBuffer` should obtain data.

`dataLength`  

Number of relevant data bytes, starting at `offsetToData`, within the source `CMBlockBuffer`. If zero, the target buffer’s total available `dataLength` (starting at offsetToData) will be referenced.

`flags`  

Feature and control flags.

`blockBufferOut`  

Receives newly-created `CMBlockBuffer` object with a retain count of 1. Must not be `NULL`.

## Return Value

Returns `kCMBlockBufferNoErr` if successful.

## Discussion

Produces a `CMBlockBuffer` containing a contiguous copy of or reference to the data specified by the parameters. The resulting new `CMBlockBuffer` may contain an allocated copy of the data, or may contain a contiguous `CMBlockBuffer` reference. If the `kCMBlockBufferAlwaysCopyDataFlag` is set in the flags parameter, the resulting `CMBlockBuffer` will contain an allocated copy of the data rather than a reference to the `SourceBuffer`.

## See Also

### Creating a Block Buffer

func CMBlockBufferCreateEmpty(allocator: CFAllocator?, capacity: UInt32, flags: CMBlockBufferFlags, blockBufferOut: UnsafeMutablePointer&lt;CMBlockBuffer?>) -> OSStatus

Creates an empty block buffer.

func CMBlockBufferCreateWithMemoryBlock(allocator: CFAllocator?, memoryBlock: UnsafeMutableRawPointer?, blockLength: Int, blockAllocator: CFAllocator?, customBlockSource: UnsafePointer&lt;CMBlockBufferCustomBlockSource>?, offsetToData: Int, dataLength: Int, flags: CMBlockBufferFlags, blockBufferOut: UnsafeMutablePointer&lt;CMBlockBuffer?>) -> OSStatus

Creates a block buffer that’s backed by a memory block.

func CMBlockBufferCreateWithBufferReference(allocator: CFAllocator?, referenceBuffer: CMBlockBuffer, offsetToData: Int, dataLength: Int, flags: CMBlockBufferFlags, blockBufferOut: UnsafeMutablePointer&lt;CMBlockBuffer?>) -> OSStatus

Creates a block buffer that refers to another block buffer object.

typealias CMBlockBufferFlags

A type for flags that control behaviors and features of block buffer APIs.

Block Buffer Flags

An enumeration of flags that control behaviors and features of block buffer APIs.

struct CMBlockBufferCustomBlockSource

A structure to support custom memory allocation and deallocation for a block used in a block buffer.

Custom Block Source Version

A custom block source version identifier.

