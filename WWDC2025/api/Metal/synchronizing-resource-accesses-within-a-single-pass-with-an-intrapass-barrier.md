*   [Metal](/documentation/metal)
*   [Resource Synchronization](/documentation/metal/resource-synchronization)
*   Synchronizing resource accesses within a single pass with an intrapass barrier

Article

# Synchronizing resource accesses within a single pass with an intrapass barrier

Resolve resource access conflicts between stages within a single pass by adding an intrapass barrier.

## [Overview](/documentation/Metal/synchronizing-resource-accesses-within-a-single-pass-with-an-intrapass-barrier#overview)

An intrapass barrier resolves access conflicts between commands within the same pass, without affecting any other passes. Apps create an access conflict when they encode commands for different passes, or different stages within a single pass, that access the same resource, and at least one command that modifies a common resource. This conflict happens because the GPU can run multiple things at the same time including:

*   Multiple passes
    
*   Different stages of a pass, such as the [`blit`](/documentation/metal/mtlstages/blit) and [`dispatch`](/documentation/metal/mtlstages/dispatch) stages of a compute pass
    
*   Multiple instances of a stage, such as two or more dispatch commands within a compute pass
    

For more information about resource access conflicts and GPU stages, see [Resource Synchronization](/documentation/metal/resource-synchronization) and [`MTLStages`](/documentation/metal/mtlstages), respectively.

Start by identifying which accesses from different stages within a pass introduce a conflict and resolve it by adding a intrapass barrier, which forces the GPU to pause before running the consuming stage until it finishes running the producing stage.

### [Identify an access conflict between two or more stages within a single pass](/documentation/Metal/synchronizing-resource-accesses-within-a-single-pass-with-an-intrapass-barrier#Identify-an-access-conflict-between-two-or-more-stages-within-a-single-pass)

The following code example encodes a compute pass that has an access conflict between its copy and dispatch commands.

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
func encodeComputeWorkWithIntrapassBarrier(computeEncoder: MTL4ComputeCommandEncoder,
```
```
                                           argumentTable: MTL4ArgumentTable,
                                           buffers: [MTLBuffer])
{
    // Assign the argument table to the compute encoder.
    computeEncoder.setArgumentTable(argumentTable)
    // Add the buffers to the argument table.
    let bufferA = buffers[0]
    let bufferB = buffers[1]
    argumentTable.setAddress(bufferA.gpuAddress, index: 0)
    argumentTable.setAddress(bufferB.gpuAddress, index: 1)
    // Encode a copy command, which the GPU runs during the blit stage.
    computeEncoder.copy(sourceBuffer: bufferA, sourceOffset: 0,
                        destinationBuffer: bufferB, destinationOffset: 0,
                        size: copySize)
    // This method needs a barrier here.
    // Run a dispatch command that works with `bufferB`,
    // which the GPU runs during the dispatch stage.
    computeEncoder.setComputePipelineState(modifyBufferIndex1ComputePipeline)
    computeEncoder.dispatchThreadgroups(threadgroupsPerGrid: threadgroupCount,
                                        threadsPerThreadgroup: threadsPerThreadgroup)
}
```
```
```
```
```

```

```
- (void)encodeComputeWorkWithIntrapassBarrier:(id<MTL4ComputeCommandEncoder>)computeEncoder
                                argumentTable:(id<MTL4ArgumentTable>)argumentTable
                                      buffers:(id<MTLBuffer> *)buffers
{
    // Assign the argument table to the compute encoder.
    [computeEncoder setArgumentTable:argumentTable];
    // Add the buffers to the argument table.
    id<MTLBuffer> bufferA = buffers[0];
    id<MTLBuffer> bufferB = buffers[1];
    [argumentTable setAddress:bufferA.gpuAddress atIndex:0];
    [argumentTable setAddress:bufferB.gpuAddress atIndex:1];
    // Encode a copy command, which the GPU runs during the blit stage.
    [computeEncoder copyFromBuffer:bufferA sourceOffset:0
                          toBuffer:bufferB destinationOffset:0
                              size:copySize];
    // This method needs a barrier here.
    // Run a dispatch command that works with `bufferB`,
    // which the GPU runs during the dispatch stage.
    [computeEncoder setComputePipelineState:modifyBufferIndex1ComputePipeline];
    [computeEncoder dispatchThreadgroups:threadgroupCount
                   threadsPerThreadgroup:threadsPerThreadgroup];
}
```

```
```
```
```
```

The example has at least one access conflict because:

*   The pass accesses the same communal resources, `bufferA` and `bufferB`, from different stages:
    
*   At least one command modifies one or more of those communal resources
    

The copy command and the dispatch commands run during the blit and dispatch stages, respectively, and both commands modify `bufferB`.

![](https://docs-assets.developer.apple.com/published/c561aebb95e82f882e2699eec5fa477c/synchronizing-resource-accesses-within-a-single-pass-with-an-intrapass-barrier-1%402x.png)

Without a barrier, the GPU can run the commands at any time relative to each other, including at the same time, which can yield inconsistent results in resources with access conflicts.

![](https://docs-assets.developer.apple.com/published/d51f338f01e9acac15e205d1ba45ebed/synchronizing-resource-accesses-within-a-single-pass-with-an-intrapass-barrier-2%402x.png)

### [Resolve an intrapass conflict with a barrier](/documentation/Metal/synchronizing-resource-accesses-within-a-single-pass-with-an-intrapass-barrier#Resolve-an-intrapass-conflict-with-a-barrier)

You can resolve access conflicts between commands within the same pass by adding a barrier with the encoder’s [`barrier(afterEncoderStages:beforeEncoderStages:visibilityOptions:)`](/documentation/metal/mtl4commandencoder/barrier\(afterencoderstages:beforeencoderstages:visibilityoptions:\)) method. The following code example modifies the previous one adding an intrapass barrier between the blit and dispatch stages within the pass.

    ```
    
```
// Encode a copy command, which the GPU runs during the blit stage.
    computeEncoder.copy(sourceBuffer: bufferA, sourceOffset: 0,
                        destinationBuffer: bufferB, destinationOffset: 0,
                        size: copySize)
    // Add a barrier between the copy above and the dispatch below.
    computeEncoder.barrier(afterEncoderStages: .blit,
                           beforeEncoderStages: .dispatch,
                           visibilityOptions: .device)
    // Run a dispatch command that works with `bufferB`,
    // which the GPU runs during the dispatch stage.
    computeEncoder.setComputePipelineState(modifyBufferIndex1ComputePipeline)
    computeEncoder.dispatchThreadgroups(threadgroupsPerGrid: threadgroupCount,
                                        threadsPerThreadgroup: threadsPerThreadgroup)
```

```

```
    
```
// Encode a copy command, which the GPU runs during the blit stage.
    [computeEncoder copyFromBuffer:bufferA sourceOffset:0
                          toBuffer:bufferB destinationOffset:0
                              size:copySize];
    // Add a barrier between the copy above and the dispatch below.
    [computeEncoder barrierAfterEncoderStages:MTLStageBlit
                          beforeEncoderStages:MTLStageDispatch
                            visibilityOptions:MTL4VisibilityOptionDevice];
    // Run a dispatch command that works with `bufferB`,
    // which the GPU runs during the dispatch stage.
    [computeEncoder setComputePipelineState:modifyBufferIndex1ComputePipeline];
    [computeEncoder dispatchThreadgroups:threadgroupCount
                   threadsPerThreadgroup:threadsPerThreadgroup];
```

```

The code example adds a barrier between the blit and dispatch stages because they both access `bufferB` with load or store operations. The barrier forces to the GPU to wait until the blit command completes before starting the dispatch stage.

![](https://docs-assets.developer.apple.com/published/5730800e64956f5a9090f6ea4451e8c8/synchronizing-resource-accesses-within-a-single-pass-with-an-intrapass-barrier-3%402x.png)

This behavior ensures that the store operation from the blit stage’s commands complete before the dispatch stage’s commands load from the same memory.

Note

An intrapass barrier doesn’t have any effect on any other pass, which means the GPU is free to start running commands from the next pass in the command buffer.

This is true even if the GPU is continuing to run commands from an earlier pass in the command buffer.

## [See Also](/documentation/Metal/synchronizing-resource-accesses-within-a-single-pass-with-an-intrapass-barrier#see-also)

### [Synchronization](/documentation/Metal/synchronizing-resource-accesses-within-a-single-pass-with-an-intrapass-barrier#Synchronization)

[

Synchronizing resource accesses between multiple passes with a fence](/documentation/metal/synchronizing-resource-accesses-between-multiple-passes-with-a-fence)

Resolve resource access conflicts between multiple passes within a single command queue by signaling a fence in one pass and waiting for it in another.

[

Synchronizing resource accesses with earlier passes with a consumer-based queue barrier](/documentation/metal/synchronizing-resource-accesses-with-earlier-passes-with-a-consumer-based-queue-barrier)

Resolve resource access conflicts between multiple passes within a single command queue by creating a consumer-based intraqueue barrier.

[

Synchronizing resource accesses with subsequent passes with a producer-based queue barrier](/documentation/metal/synchronizing-resource-accesses-with-subsequent-passes-with-a-producer-based-queue-barrier)

Resolve resource access conflicts between multiple passes within a single command queue by creating a producer-based intraqueue barrier.

[

Synchronizing CPU and GPU Work](/documentation/metal/synchronizing-cpu-and-gpu-work)

Avoid stalls between CPU and GPU work by using multiple instances of a resource.

[

Implementing a Multistage Image Filter Using Heaps and Fences](/documentation/metal/implementing-a-multistage-image-filter-using-heaps-and-fences)

Use fences to synchronize access to resources allocated on a heap.

```swift
```swift
```swift
struct MTLStages
```
```

Describes stages of GPU work.

Beta
```
```swift
```swift
```swift
protocol MTLFence
```
```

A memory fence to capture, track, and manage resource dependencies across command encoders.
```
```swift
```swift
```swift
struct MTLRenderStages
```
```

The stages in a render pass that triggers a synchronization command.
```
```swift
```swift
```swift
struct MTLBarrierScope
```
```

Describes the types of resources that a barrier operates on.
```
```swift
```swift
```swift
struct MTL4VisibilityOptions
```
```

Memory consistency options for synchronization commands.

Beta
```