Collection

*   [Metal](/documentation/metal)
*   Resource Loading

API Collection

# Resource Loading

Load assets in your games and apps quickly by running a dedicated input/output queue alongside your GPU tasks.

## [Overview](/documentation/Metal/resource-loading#overview)

Metal 3 adds input/output command queues and buffers that make the most of a device’s storage hardware, including flash storage and the unified memory architecture of Apple silicon, when available. When you run a dedicated input/output queue alongside your GPU tasks, you can synchronize them with Metal shared events. With this approach, you can minimize load screen times by fetching the essential assets first and streaming the rest as you need them. You can also start multiple input/output command buffers to load different asset batches and later cancel the ones you don’t need. Ensure that time-sensitive assets, such as sound effects, load with lower latency by running those command buffers on higher-priority queues that you create.

First, create [`MTLIOCommandQueue`](/documentation/metal/mtliocommandqueue) instances by configuring an [`MTLIOCommandQueueDescriptor`](/documentation/metal/mtliocommandqueuedescriptor) instance and passing it to an [`MTLDevice`](/documentation/metal/mtldevice) instance’s [`makeIOCommandQueue(descriptor:)`](/documentation/metal/mtldevice/makeiocommandqueue\(descriptor:\)) method.

```swift

```swift
// Create a Metal I/O command queue.
```swift
```swift
let commandQueueDescriptor = MTLIOCommandQueueDescriptor()
```
```
commandQueueDescriptor.type = .concurrent
commandQueueDescriptor.priority = .normal
```swift
```swift
let ioCommandQueue = try device.makeIOCommandQueue(descriptor:
```
```
                                                    commandQueueDescriptor)
```

```

```

```
// Create a Metal I/O command queue.
MTLIOCommandQueueDescriptor *commandQueueDescriptor;
commandQueueDescriptor = [[MTLIOCommandQueueDescriptor alloc] init];
commandQueueDescriptor.type = MTLIOCommandQueueTypeConcurrent;
commandQueueDescriptor.priority = MTLIOPriorityNormal;
NSError *error = nil;
id<MTLIOCommandQueue> ioCommandQueue;
ioCommandQueue = [device newIOCommandQueueWithDescriptor:commandQueueDescriptor
                                                   error:&error];
if (error != nil) {
        // Report the error.
        ...
}
```

```

For each queue, create one or more [`MTLIOCommandBuffer`](/documentation/metal/mtliocommandbuffer) instances by calling the queue’s [`makeCommandBuffer()`](/documentation/metal/mtliocommandqueue/makecommandbuffer\(\)) or [`makeCommandBufferWithUnretainedReferences()`](/documentation/metal/mtliocommandqueue/makecommandbufferwithunretainedreferences\(\)) method. For each command buffer, load the assets you want by calling any of the [`MTLIOCommandBuffer`](/documentation/metal/mtliocommandbuffer) protocol’s load methods. For example:

*   The [`load(_:offset:size:sourceHandle:sourceHandleOffset:)`](/documentation/metal/mtliocommandbuffer/load\(_:offset:size:sourcehandle:sourcehandleoffset:\)) method loads an asset into an [`MTLBuffer`](/documentation/metal/mtlbuffer).
    
*   The [`load(_:slice:level:size:sourceBytesPerRow:sourceBytesPerImage:destinationOrigin:sourceHandle:sourceHandleOffset:)`](/documentation/metal/mtliocommandbuffer/load\(_:slice:level:size:sourcebytesperrow:sourcebytesperimage:destinationorigin:sourcehandle:sourcehandleoffset:\)) method loads an asset into an [`MTLTexture`](/documentation/metal/mtltexture).
    
*   The [`loadBytes(_:size:sourceHandle:sourceHandleOffset:)`](/documentation/metal/mtliocommandbuffer/loadbytes\(_:size:sourcehandle:sourcehandleoffset:\)) method loads an asset, such as an audio file, into a CPU-accessible memory buffer.
    

```swift

```swift
// Create a Metal I/O command buffer.
```swift
```swift
let ioCommandBuffer = ioCommandQueue.makeCommandBuffer()
```
```
// Encode a command that loads a texture.
ioCommandBuffer.load(texture,
                     slice: 0,
                     level: 0,
                     size: textureSize,
                     sourceBytesPerRow: bytesPerRow,
                     sourceBytesPerImage: bytesPerImage,
                     destinationOrigin: origin,
                     sourceHandle: fileHandle,
                     sourceHandleOffset: 0)
// Encode a command that loads a buffer.
ioCommandBuffer.load(buffer,
                     offset: 0,
                     size: bufferSize,
                     sourceHandle: fileHandle,
                     sourceHandleOffset: 0)
// Submit the command buffer to run.
ioCommandBuffer.commit()
```

```

```

```
// Create a Metal I/O command buffer.
id<MTLIOCommandBuffer> ioCommandBuffer = [ioCommandQueue commandBuffer];
// Encode a command that loads a texture.
[ioCommandBuffer loadTexture:texture
                       slice:0
                       level:0
                        size:textureSize
           sourceBytesPerRow:bytesPerRow
         sourceBytesPerImage:bytesPerImage
           destinationOrigin:origin
                sourceHandle:textureAssetHandle
          sourceHandleOffset:0];
// Encode a command that loads a buffer.
[ioCommandBuffer loadBuffer:buffer
                     offset:0
                       size:bufferSize
               sourceHandle:bufferAssetHandle
         sourceHandleOffset:0];
// Submit the command buffer to run.
[ioCommandBuffer commit];
```

```

For each asset, create an [`MTLIOFileHandle`](/documentation/metal/mtliofilehandle) instance using the input/output command buffer’s load methods. To create a file handle for your asset, call an [`MTLDevice`](/documentation/metal/mtldevice) instance’s [`makeIOHandle(url:)`](/documentation/metal/mtldevice/makeiohandle\(url:\)) or [`makeIOHandle(url:compressionMethod:)`](/documentation/metal/mtldevice/makeiohandle\(url:compressionmethod:\)) method.

```swift
```swift
```swift
```swift
```swift
```swift
```swift
```swift
```swift
```swift
```swift
func createHandleForFile(at url: URL, with device: MTLDevice) -> MTLIOFileHandle? {
```
```
    return try? device.makeIOHandle(url: url)
}
```
```
```
```
```

```

```
id<MTLIOFileHandle> createHandleForFile(NSURL *url, id<MTLDevice> device)
{
    NSError *error = nil;
    id<MTLIOFileHandle> assetHandle = [device newIOHandleWithURL:url error:&error];
    if (error != nil) {
        // Report the error.
        ...
    }
    return assetHandle;
}
```

```
```
```
```
```

Note

You must create each file handle using the same [`MTLDevice`](/documentation/metal/mtldevice) instance that created the [`MTLIOCommandQueue`](/documentation/metal/mtliocommandqueue) and [`MTLIOCommandBuffer`](/documentation/metal/mtliocommandbuffer) instances that load the files.

To help minimize your appʼs storage footprint, compress your assets at development time. First, create a new compression context with the [`MTLIOCreateCompressionContext`](/documentation/metal/mtliocreatecompressioncontext) function. Then, add data for an asset to the compression context using the [`MTLIOCompressionContextAppendData(_:_:_:)`](/documentation/metal/mtliocompressioncontextappenddata\(_:_:_:\)) function. Finally, call the  [`MTLIOFlushAndDestroyCompressionContext(_:)`](/documentation/metal/mtlioflushanddestroycompressioncontext\(_:\)) function to save the context to a compressed file that you add to your project.

## [Topics](/documentation/Metal/resource-loading#topics)

### [I/O Command Queues](/documentation/Metal/resource-loading#IO-Command-Queues)

```swift
```swift
```swift
```swift
protocol MTLIOCommandQueue
```
```

A command queue that schedules input/output commands for reading files in the file system, and writing to GPU resources and memory.
```
```swift
```swift
```swift
class MTLIOCommandQueueDescriptor
```
```

A configuration template you use to create a new input/output command queue.
```
```swift
```swift
```swift
enum MTLIOPriority
```
```

Designates the priority for a new input/output command queue.
```
```swift
```swift
```swift
enum MTLIOCommandQueueType
```
```

Designates the queue type for a new input/output command queue.
```
```swift
```swift
```swift
protocol MTLIOScratchBufferAllocator
```
```

A protocol your app implements to provide scratch memory to an input/output command queue.
```
```swift
```swift
```swift
protocol MTLIOScratchBuffer
```
```

A protocol your app implements that wraps a Metal buffer instance to serve as scratch memory for an input/output command queue.
```
```

### [I/O Command Buffers](/documentation/Metal/resource-loading#IO-Command-Buffers)

```swift
```swift
```swift
```swift
protocol MTLIOCommandBuffer
```
```

A command buffer that contains input/output commands that work with files in the file systems and Metal resources.
```
```swift
```swift
```swift
protocol MTLIOFileHandle
```
```

Represents a raw or compressed file, such as a resource asset file in your app’s bundle.
```
```swift
```swift
```swift
typealias MTLIOCommandBufferHandler
```
```

A convenience type that defines the signature of an input/output command buffer’s completion handler.
```
```swift
```swift
```swift
enum MTLIOStatus
```
```

Represents the state of an input/output command buffer.
```
```swift
```swift
```swift
enum Code
```
```

The error codes for creating an input/output file handle.
```
```swift
```swift
```swift
let MTLIOErrorDomain: String
```
```

The domain for input/output command queue errors.
```
```

### [Asset Compression](/documentation/Metal/resource-loading#Asset-Compression)

```swift
```swift
```swift
```swift
func MTLIOCreateCompressionContext(String, MTLIOCompressionMethod, Int) -> MTLIOCompressionContext?
```
```

Creates a compression context that you use to compress data into a single file.
```
```swift
```swift
```swift
enum MTLIOCompressionMethod
```
```

The compression codecs that Metal supports for input/output handles.
```
```swift
```swift
```swift
func MTLIOCompressionContextDefaultChunkSize() -> Int
```
```

Returns a compression chunk size you can use as a default for creating a compression context.
```
```swift
```swift
```swift
typealias MTLIOCompressionContext
```
```

A pointer that represents the state of a file compression session in progress.
```
```swift
```swift
```swift
func MTLIOCompressionContextAppendData(MTLIOCompressionContext, UnsafeRawPointer, Int)
```
```

Adds data to a compression context.
```
```swift
```swift
```swift
func MTLIOFlushAndDestroyCompressionContext(MTLIOCompressionContext) -> MTLIOCompressionStatus
```
```

Finishes compressing and saves the file that a compression context represents.
```
```swift
```swift
```swift
enum MTLIOCompressionStatus
```
```

Represents the final state of a compression context.
```
```

## [See Also](/documentation/Metal/resource-loading#see-also)

### [Resources](/documentation/Metal/resource-loading#Resources)

[

API Reference

Resource Fundamentals](/documentation/metal/resource-fundamentals)

Control the common attributes of all Metal memory resources, including buffers and textures, and how to configure their underlying memory.

[

API Reference

Buffers](/documentation/metal/buffers)

Create and manage untyped data your app uses to exchange information with its shader functions.

[

API Reference

Textures](/documentation/metal/textures)

Create and manage typed data your app uses to exchange information with its shader functions.

[

API Reference

Memory Heaps](/documentation/metal/memory-heaps)

Take control of your app’s GPU memory management by creating a large memory allocation for various buffers, textures, and other resources.

[

API Reference

Resource Synchronization](/documentation/metal/resource-synchronization)

Prevent multiple commands that can access the same resources simultaneously by coordinating those accesses with barriers, fences, or events.