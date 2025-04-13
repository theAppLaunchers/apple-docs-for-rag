

- Metal
- MTLRenderCommandEncoder
-  setFragmentBuffers(\_:offsets:range:) 

Instance Method

# setFragmentBuffers(\_:offsets:range:)

Assigns multiple buffers to a range of entries in the fragment shader argument table.

iOS 8.0+iPadOS 8.0+Mac CatalystmacOS 10.11+tvOS 8.0+visionOS

``` source
func setFragmentBuffers(
    _ buffers: [(any MTLBuffer)?],
    offsets: [Int],
    range: Range
)
```

## Parameters 

`buffers`  

An array of MTLBuffer instances the command assigns to entries in the fragment shader argument table for buffers.

`offsets`  

An array of integers. Each element represents the location, in bytes, from the start of the corresponding MTLBuffer element in `buffers` where the fragment shader argument data begins.

See the Metal feature set tables (PDF) to check for offset alignment requirements for buffers in `device` and `constant` address space.

`range`  

A span of integers that represent the entries in the fragment shader argument table for buffers. Each entry stores a record of the corresponding element in `buffers` and `offsets`.

## Discussion

By default, the buffer at each index is `nil`.

Note

The Objective-C version of this method is setFragmentBuffers:offsets:withRange:.

## See Also

### Assigning Buffers

func setFragmentBuffer((any MTLBuffer)?, offset: Int, index: Int)

Assigns a buffer to an entry in the fragment shader argument table.

**Required**

func setFragmentBytes(UnsafeRawPointer, length: Int, index: Int)

Creates a buffer from bytes and assigns it to an entry in the fragment shader argument table.

**Required**

func setFragmentBufferOffset(Int, index: Int)

Updates an entry in the fragment shader argument table with a new location within the entry’s current buffer.

**Required**

