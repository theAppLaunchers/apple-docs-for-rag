

- Core Media
-  CMBlockBufferCreateEmpty(allocator:capacity:flags:blockBufferOut:) 

Function

# CMBlockBufferCreateEmpty(allocator:capacity:flags:blockBufferOut:)

Creates an empty block buffer.

iOS 4.0+iPadOS 4.0+Mac Catalyst 13.1+macOS 10.7+tvOS 9.0+visionOS 1.0+watchOS 6.0+

``` source
func CMBlockBufferCreateEmpty(
    allocator structureAllocator: CFAllocator?,
    capacity subBlockCapacity: UInt32,
    flags: CMBlockBufferFlags,
    blockBufferOut: UnsafeMutablePointer
) -> OSStatus
```

## Parameters 

`structureAllocator`  

Allocator to use for allocating the `CMBlockBuffer` object. `NULL` will cause the default allocator to be used.

`subBlockCapacity`  

Number of sub-blocks the new `CMBlockBuffer` shall accommodate before expansion occurs. A value of zero means “do the reasonable default”.

`flags`  

Feature and control flags.

`blockBufferOut`  

Receives newly-created empty `CMBlockBuffer` object with retain count of 1. Must not be `NULL`.

## Return Value

Returns `kCMBlockBufferNoErr` if successful.

## Discussion

Creates an empty `CMBlockBuffer`, i.e. one which has no memory block nor reference to a `CMBlockBuffer` supplying bytes to it. It is ready to be populated using `CMBlockBufferAppendMemoryBlock`() and/or `CMBlockBufferAppendBufferReference`. `CMBlockBufferGetDataLength` will return zero for an empty `CMBlockBuffer` and `CMBlockBufferGetDataPointer` and `CMBlockBufferAssureBufferMemory` will fail.The memory for the `CMBlockBuffer` object will be allocated using the given allocator. If `NULL` is passed for the allocator, the default allocator is used.

## See Also

### Creating a Block Buffer

func CMBlockBufferCreateWithMemoryBlock(allocator: CFAllocator?, memoryBlock: UnsafeMutableRawPointer?, blockLength: Int, blockAllocator: CFAllocator?, customBlockSource: UnsafePointer&lt;CMBlockBufferCustomBlockSource>?, offsetToData: Int, dataLength: Int, flags: CMBlockBufferFlags, blockBufferOut: UnsafeMutablePointer&lt;CMBlockBuffer?>) -> OSStatus

Creates a block buffer that’s backed by a memory block.

func CMBlockBufferCreateWithBufferReference(allocator: CFAllocator?, referenceBuffer: CMBlockBuffer, offsetToData: Int, dataLength: Int, flags: CMBlockBufferFlags, blockBufferOut: UnsafeMutablePointer&lt;CMBlockBuffer?>) -> OSStatus

Creates a block buffer that refers to another block buffer object.

func CMBlockBufferCreateContiguous(allocator: CFAllocator?, sourceBuffer: CMBlockBuffer, blockAllocator: CFAllocator?, customBlockSource: UnsafePointer&lt;CMBlockBufferCustomBlockSource>?, offsetToData: Int, dataLength: Int, flags: CMBlockBufferFlags, blockBufferOut: UnsafeMutablePointer&lt;CMBlockBuffer?>) -> OSStatus

Creates a block buffer that contains a contiguous copy of, or reference to, the data specified by the parameters.

typealias CMBlockBufferFlags

A type for flags that control behaviors and features of block buffer APIs.

Block Buffer Flags

An enumeration of flags that control behaviors and features of block buffer APIs.

struct CMBlockBufferCustomBlockSource

A structure to support custom memory allocation and deallocation for a block used in a block buffer.

Custom Block Source Version

A custom block source version identifier.

