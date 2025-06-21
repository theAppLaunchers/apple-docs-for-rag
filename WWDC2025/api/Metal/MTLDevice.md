*   [Metal](/documentation/metal)
*   MTLDevice

Protocol

# MTLDevice

The main Metal interface to a GPU that apps use to draw graphics and run computations in parallel.

iOS 8.0+iPadOS 8.0+Mac Catalyst 13.1+macOS 10.11+tvOSvisionOS 1.0+

```swift
```swift
```swift
```swift
```swift
```swift
```swift
```swift
protocol MTLDevice : [`NSObjectProtocol`](/documentation/ObjectiveC/NSObjectProtocol), [`Sendable`](/documentation/Swift/Sendable)
```
```
```
```
```
```
```
```

## [Mentioned in](/documentation/Metal/MTLDevice#mentions)

[

Understanding the Metal 4 core API](/documentation/metal/understanding-the-metal-4-core-api)

[

Finding Multiple GPUs on an Intel-based Mac](/documentation/metal/finding-multiple-gpus-on-an-intel-based-mac)

[

Developing Metal apps that run in Simulator](/documentation/metal/developing-metal-apps-that-run-in-simulator)

[

Getting the Default GPU](/documentation/metal/getting-the-default-gpu)

[

Detecting GPU Features and Metal Software Versions](/documentation/metal/detecting-gpu-features-and-metal-software-versions)

## [Overview](/documentation/Metal/MTLDevice#overview)

You can get the default [`MTLDevice`](/documentation/metal/mtldevice) at runtime by calling [`MTLCreateSystemDefaultDevice()`](/documentation/metal/mtlcreatesystemdefaultdevice\(\)) (see [Getting the Default GPU](/documentation/metal/getting-the-default-gpu)). Each Metal device instance represents a GPU and is the main starting point for your app’s interaction with it. With a Metal device instance, you can inspect a GPU’s features and capabilities (see [Device Inspection](/documentation/metal/device-inspection)) and create subsidiary type instances with its factory methods.

*   Buffers, textures, and other resources store, synchronize, and pass data between the GPU and CPU (see [Resource Fundamentals](/documentation/metal/resource-fundamentals)).
    
*   Input/Output command queues efficiently load resources from the file system (see [Resource Loading](/documentation/metal/resource-loading)).
    
*   Command queues create command encoders and schedule work for the GPU, including rendering and compute commands (see [Render Passes](/documentation/metal/render-passes) and [Compute Passes](/documentation/metal/compute-passes)).
    
*   Pipeline states store render or compute pipeline configurations — which can be expensive to create — so that you can reuse them, potentially many times.
    

If your app uses more than one GPU (see [Multi-GPU Systems](/documentation/metal/multi-gpu-systems)), ensure that instances of these types only interact with others from the same device. For example, your app can pass a texture to a command encoder that comes from the same Metal device, but not to another device.

## [Topics](/documentation/Metal/MTLDevice#topics)

### [Working with GPU Devices](/documentation/Metal/MTLDevice#Working-with-GPU-Devices)

[

API Reference

Device Inspection](/documentation/metal/device-inspection)

Locate and identify a GPU and the features it supports, and sample its counters.

[

API Reference

Work Submission](/documentation/metal/work-submission)

Create queues that submit work to the GPU or load assets into GPU resources, and indirect command buffers that group your frequent commands together.

[

API Reference

Pipeline State Creation](/documentation/metal/pipeline-state-creation)

Create pipeline states for render and compute passes, samplers, depth and stencil states, and indirect command buffers.

[

API Reference

Resource Creation](/documentation/metal/resource-creation)

Load assets with input/output queues and make various resource instances, such as buffers, textures, acceleration structures, and memory heaps.

[

API Reference

Shader Library and Archive Creation](/documentation/metal/shader-library-and-archive-creation)

Create static and dynamic shader libraries, and binary shader archives.

### [Instance Properties](/documentation/Metal/MTLDevice#Instance-Properties)

```swift
```swift
```swift
```swift
var maximumConcurrentCompilationTaskCount: Int
```
```

The maximum number of concurrent compilation tasks the device is running.

**Required**
```
```swift
```swift
```swift
var shouldMaximizeConcurrentCompilation: Bool
```
```

A Boolean value that indicates whether the device uses additional CPU threads for compilation tasks.

**Required**
```
```

### [Instance Methods](/documentation/Metal/MTLDevice#Instance-Methods)

```swift
```swift
```swift
```swift
func functionHandle(function: any MTLFunction) -> (any MTLFunctionHandle)?
```
```

**Required**

Beta
```
```swift
```swift
```swift
func functionHandle(function: any MTL4BinaryFunction) -> (any MTLFunctionHandle)?
```
```

Get the function handle for the specified binary-linked function from the pipeline state.

**Required**

Beta
```
```swift
```swift
```swift
func makeArchive(url: URL) throws -> any MTL4Archive
```
```

Creates a new archive from data available at an `NSURL` address.

**Required**

Beta
```
```swift
```swift
```swift
func makeArgumentTable(descriptor: MTL4ArgumentTableDescriptor) throws -> any MTL4ArgumentTable
```
```

Creates a new argument table from an argument table descriptor.

**Required**

Beta
```
```swift
```swift
```swift
func makeBuffer(length: Int, options: MTLResourceOptions, placementSparsePageSize: MTLSparsePageSize) -> (any MTLBuffer)?
```
```

Creates a new placement sparse buffer of a specific length.

**Required**

Beta
```
```swift
```swift
```swift
func makeCommandAllocator() -> (any MTL4CommandAllocator)?
```
```

Creates a new command allocator.

**Required**

Beta
```
```swift
```swift
```swift
func makeCommandAllocator(descriptor: MTL4CommandAllocatorDescriptor) throws -> any MTL4CommandAllocator
```
```

Creates a new command allocator from a command allocator descriptor.

**Required**

Beta
```
```swift
```swift
```swift
func makeCommandBuffer() -> (any MTL4CommandBuffer)?
```
```

Creates a new command buffer.

**Required**

Beta
```
```swift
```swift
```swift
func makeCommandQueue(descriptor: MTLCommandQueueDescriptor) -> (any MTLCommandQueue)?
```
```

Creates a command queue with the provided configuration.

**Required**
```
```swift
```swift
```swift
func makeCompiler(descriptor: MTL4CompilerDescriptor) throws -> any MTL4Compiler
```
```

Creates a new compiler from a compiler descriptor.

**Required**

Beta
```
```swift
```swift
```swift
func makeCounterHeap(descriptor: MTL4CounterHeapDescriptor) throws -> any MTL4CounterHeap
```
```

Creates a new counter heap configured from a counter heap descriptor.

**Required**

Beta
```
```swift
```swift
```swift
func makeLogState(descriptor: MTLLogStateDescriptor) throws -> any MTLLogState
```
```

Creates a shader log state with the provided configuration.

**Required**
```
```swift
```swift
```swift
func makeMTL4CommandQueue() -> (any MTL4CommandQueue)?
```
```

Creates a new command queue.

**Required**

Beta
```
```swift
```swift
```swift
func makeMTL4CommandQueue(descriptor: MTL4CommandQueueDescriptor) throws -> any MTL4CommandQueue
```
```

Creates a new command queue from a queue descriptor.

**Required**

Beta
```
```swift
```swift
```swift
func makePipelineDataSetSerializer(descriptor: MTL4PipelineDataSetSerializerDescriptor) -> any MTL4PipelineDataSetSerializer
```
```

Creates a new pipeline data set serializer instance from a descriptor.

**Required**

Beta
```
```swift
```swift
```swift
func makeTensor(descriptor: MTLTensorDescriptor) throws -> any MTLTensor
```
```

Creates a tensor by allocating new memory.

**Required**

Beta
```
```swift
```swift
```swift
func makeTextureViewPool(descriptor: MTLResourceViewPoolDescriptor) throws -> any MTLTextureViewPool
```
```

Creates a new texture view pool from a resource view pool descriptor.

**Required**

Beta
```
```swift
```swift
```swift
func queryTimestampFrequency() -> UInt64
```
```

Queries the frequency of the GPU timestamp in ticks per second.

**Required**

Beta
```
```swift
```swift
```swift
func size(ofCounterHeapEntry: MTL4CounterHeapType) -> Int
```
```

Returns the size, in bytes, of each entry in a counter heap of a specific counter heap type when your app resolves it into a usable format.

**Required**

Beta
```
```swift
```swift
```swift
func tensorSizeAndAlign(descriptor: MTLTensorDescriptor) -> MTLSizeAndAlign
```
```

Determines the size and alignment required to hold the data of a tensor you create with a descriptor in a buffer.

**Required**

Beta
```
```

## [Relationships](/documentation/Metal/MTLDevice#relationships)

### [Inherits From](/documentation/Metal/MTLDevice#inherits-from)

*   [`NSObjectProtocol`](/documentation/ObjectiveC/NSObjectProtocol)
*   [`Sendable`](/documentation/Swift/Sendable)
*   [`SendableMetatype`](/documentation/Swift/SendableMetatype)

## [See Also](/documentation/Metal/MTLDevice#see-also)

### [Locating and Inspecting a GPU Device](/documentation/Metal/MTLDevice#Locating-and-Inspecting-a-GPU-Device)

[

Getting the Default GPU](/documentation/metal/getting-the-default-gpu)

Select the system’s default GPU device on which to run your Metal code.

[

Detecting GPU Features and Metal Software Versions](/documentation/metal/detecting-gpu-features-and-metal-software-versions)

Use the device object’s properties to determine how you perform tasks in Metal.

```swift
```swift
```swift
func MTLCreateSystemDefaultDevice() -> (any MTLDevice)?
```
```

Returns the device instance Metal selects as the default.
```

[

API Reference

Multi-GPU Systems](/documentation/metal/multi-gpu-systems)

Locate and work with internal and external GPUs and their displays, video memory, and performance tradeoffs.