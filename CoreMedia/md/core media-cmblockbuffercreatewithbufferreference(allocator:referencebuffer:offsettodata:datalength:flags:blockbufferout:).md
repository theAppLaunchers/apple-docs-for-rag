

- Core Media
-  CMBlockBufferCreateWithBufferReference(allocator:referenceBuffer:offsetToData:dataLength:flags:blockBufferOut:) 

Function

# CMBlockBufferCreateWithBufferReference(allocator:referenceBuffer:offsetToData:dataLength:flags:blockBufferOut:)

Creates a block buffer that refers to another block buffer object.

iOS 4.0+iPadOS 4.0+Mac Catalyst 13.1+macOS 10.7+tvOS 9.0+visionOS 1.0+watchOS 6.0+

``` source
func CMBlockBufferCreateWithBufferReference(
    allocator structureAllocator: CFAllocator?,
    referenceBuffer bufferReference: CMBlockBuffer,
    offsetToData: Int,
    dataLength: Int,
    flags: CMBlockBufferFlags,
    blockBufferOut: UnsafeMutablePointer
) -> OSStatus
```

## Parameters 

`structureAllocator`  

Allocator to use for allocating the `CMBlockBuffer` object. `NULL` will cause the default allocator to be used.

`bufferReference`  

The target `CMBlockBuffer`. This parameter must not be `NULL`. Unless the `kCMBlockBufferPermitEmptyReferenceFlag` is passed, it must not be empty and it must have a data length at least large enough to supply the data subset specified (i.e. offsetToData+dataLength bytes).

`offsetToData`  

Offset within the target `CMBlockBuffer` at which the new `CMBlockBuffer` should refer to data.

`dataLength`  

Number of relevant data bytes, starting at `offsetToData`, within the target `CMBlockBuffer`.

`flags`  

Feature and control flags.

`blockBufferOut`  

Receives newly-created `CMBlockBuffer` object with a retain count of 1. Must not be `NULL`.

## Return Value

Returns `kCMBlockBufferNoErr` if successful.

## Discussion

Creates a new `CMBlockBuffer` that refers to (a possibly subset portion of) another `CMBlockBuffer`. The returned `CMBlockBuffer` may be further expanded using CMBlockBufferAppendMemoryBlock(_:memoryBlock:length:blockAllocator:customBlockSource:offsetToData:dataLength:flags:) and/or CMBlockBufferAppendBufferReference(_:targetBBuf:offsetToData:dataLength:flags:).

## See Also

### Creating a Block Buffer

func CMBlockBufferCreateEmpty(allocator: CFAllocator?, capacity: UInt32, flags: CMBlockBufferFlags, blockBufferOut: UnsafeMutablePointer&lt;CMBlockBuffer?>) -> OSStatus

Creates an empty block buffer.

func CMBlockBufferCreateWithMemoryBlock(allocator: CFAllocator?, memoryBlock: UnsafeMutableRawPointer?, blockLength: Int, blockAllocator: CFAllocator?, customBlockSource: UnsafePointer&lt;CMBlockBufferCustomBlockSource>?, offsetToData: Int, dataLength: Int, flags: CMBlockBufferFlags, blockBufferOut: UnsafeMutablePointer&lt;CMBlockBuffer?>) -> OSStatus

Creates a block buffer that’s backed by a memory block.

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

