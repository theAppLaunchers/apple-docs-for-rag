*   [Metal](/documentation/metal)
*   [Resource Synchronization](/documentation/metal/resource-synchronization)
*   Synchronizing resource accesses with subsequent passes with a producer-based queue barrier

Article

# Synchronizing resource accesses with subsequent passes with a producer-based queue barrier

Resolve resource access conflicts between multiple passes within a single command queue by creating a producer-based intraqueue barrier.

## [Overview](/documentation/Metal/synchronizing-resource-accesses-with-subsequent-passes-with-a-producer-based-queue-barrier#overview)

Producer queue barriers are coarse synchronization primitives that resolve access conflicts between commands in different passes that you submit to the same command queue, including passes from other command buffers. Producer barriers are convenient for synchronizing passes that modify communal resources that multiple, subsequent passes in the same queue load later on.

Note

Producer barriers are only available to Metal 4 encoder types.

Apps create an access conflict when they encode commands for different passes, or different stages within a single pass, which access the same resource, and at least one command that modifies a common resource. This conflict happens because the GPU can run multiple things at the same time, including:

*   Multiple passes
    
*   Different stages of a pass, such as the [`blit`](/documentation/metal/mtlstages/blit) and [`dispatch`](/documentation/metal/mtlstages/dispatch) stages of a compute pass
    
*   Multiple instances of a stage, such as two or more dispatch commands within a compute pass
    

For more information about resource access conflicts and GPU stages, see [Resource Synchronization](/documentation/metal/resource-synchronization) and [`MTLStages`](/documentation/metal/mtlstages), respectively.

Tip

As an alternative to a producer queue barrier, you can create an intraqueue barrier in the consumer pass; for more information, see [Synchronizing resource accesses with earlier passes with a consumer-based queue barrier](/documentation/metal/synchronizing-resource-accesses-with-earlier-passes-with-a-consumer-based-queue-barrier).

Start by identifying which accesses from subsequent passes in the same queue introduce a conflict and resolve it with an intraqueue barrier in the producing pass.

### [Identify access conflicts with subsequent passes on the same queue](/documentation/Metal/synchronizing-resource-accesses-with-subsequent-passes-with-a-producer-based-queue-barrier#Identify-access-conflicts-with-subsequent-passes-on-the-same-queue)

The following code example encodes three compute passes. The first pass runs a single copy command:

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
func encodeComputeWorkWithProducerBarrier(commandBuffer: MTL4CommandBuffer,
```
```
                                          argumentTable: MTL4ArgumentTable,
                                          buffers: [MTLBuffer])
{
    // === Encode pass 1 ===
    // Create an encoder for the first compute pass.
    let computeEncoder1: MTL4ComputeCommandEncoder!
    computeEncoder1 = commandBuffer.makeComputeCommandEncoder()
    // Assign the argument table to the compute encoder.
    computeEncoder1.setArgumentTable(argumentTable)
    // Add the buffers to the argument table for the dispatch command.
    let bufferA = buffers[0]
    let bufferB = buffers[1]
    argumentTable.setAddress(bufferA.gpuAddress, index: 0)
    argumentTable.setAddress(bufferB.gpuAddress, index: 1)
    // Copy from `bufferA` to `bufferB`, which runs during the  blit stage.
    computeEncoder1.copy(sourceBuffer: bufferA, sourceOffset: 0,
                         destinationBuffer: bufferB, destinationOffset: 0,
                         size: copySize)
    // Finalize the first compute pass.
    computeEncoder1.endEncoding()
```
```
```
```
```

```

```
- (void)encodeComputeWorkWithProducerBarrier:(id<MTL4CommandBuffer>)commandBuffer
                               argumentTable:(id<MTL4ArgumentTable>)argumentTable
                                     buffers:(id<MTLBuffer> *)buffers
{
    // === Encode pass 1 ===
    // Create an encoder for the first compute pass.
    id<MTL4ComputeCommandEncoder> computeEncoder1;
    computeEncoder1 = [commandBuffer computeCommandEncoder];
    // Assign the argument table to the compute encoder.
    [computeEncoder1 setArgumentTable:argumentTable];
    // Add the buffers to the argument table for the dispatch command.
    id<MTLBuffer> bufferA = buffers[0];
    id<MTLBuffer> bufferB = buffers[1];
    [argumentTable setAddress:bufferA.gpuAddress atIndex:0];
    [argumentTable setAddress:bufferB.gpuAddress atIndex:1];
    // Copy from `bufferA` to `bufferB`, which runs during the blit stage.
    [computeEncoder1 copyFromBuffer:bufferA sourceOffset:0
                           toBuffer:bufferB destinationOffset:0
                               size:copySize];
    // Finalize the first compute pass.
    [computeEncoder1 endEncoding];
```

```
```
```
```
```

The second pass runs a copy command and a dispatch command:

    ```swift
    
```swift
// === Encode pass 2 ===
    // Create an encoder for the second compute pass.
    let computeEncoder2: MTL4ComputeCommandEncoder!
    computeEncoder2 = commandBuffer.makeComputeCommandEncoder()
    // Assign the argument table to the compute encoder.
    computeEncoder2.setArgumentTable(argumentTable)
    // Copy from `bufferC` to `bufferD`, which runs during the blit stage.
    let bufferC = buffers[2]
    let bufferD = buffers[3]
    argumentTable.setAddress(bufferC.gpuAddress, index: 2)
    argumentTable.setAddress(bufferD.gpuAddress, index: 3)
    computeEncoder2.copy(sourceBuffer: bufferC, sourceOffset: 0,
                         destinationBuffer: bufferD, destinationOffset: 0,
                         size: copySize)
    // The dispatch in pass 3 needs to wait for
    // the blit stage in pass 2 to finish.
    // Run a dispatch command that works with `bufferC`,
    // which the GPU runs during the dispatch stage.
    computeEncoder2.setComputePipelineState(modifyBufferIndex2ComputePipeline)
    computeEncoder2.dispatchThreadgroups(threadgroupsPerGrid: threadgroupCount,
                                         threadsPerThreadgroup: threadsPerThreadgroup)
    // Finalize the second compute pass.
    computeEncoder2.endEncoding()
```

```

```
    
```
// === Encode pass 2 ===
    // Create an encoder for the second compute pass.
    id<MTL4ComputeCommandEncoder> computeEncoder2;
    computeEncoder2 = [commandBuffer computeCommandEncoder];
    // Assign the argument table to the compute encoder.
    [computeEncoder2 setArgumentTable:argumentTable];
    // Copy from `bufferC` to `bufferD`, which runs during the blit stage.
    id<MTLBuffer> bufferC = buffers[2];
    id<MTLBuffer> bufferD = buffers[3];
    [argumentTable setAddress:bufferC.gpuAddress atIndex:2];
    [argumentTable setAddress:bufferD.gpuAddress atIndex:3];
    [computeEncoder2 copyFromBuffer:bufferC sourceOffset:0
                           toBuffer:bufferD destinationOffset:0
                               size:copySize];
    // The dispatch in pass 3 needs to wait for
    // the blit stage in pass 2 to finish.
    // Run a dispatch command that works with `bufferC`,
    // which the GPU runs during the dispatch stage.
    [computeEncoder2 setComputePipelineState:modifyBufferIndex2ComputePipeline];
    [computeEncoder2 dispatchThreadgroups:threadgroupCount
                    threadsPerThreadgroup:threadsPerThreadgroup];
    // Finalize the second compute pass.
    [computeEncoder2 endEncoding];
```

```

The third pass runs a single dispatch command:

    ```swift
    
```swift
// === Encode pass 3 ===
    // Create an encoder for the third compute pass.
    let computeEncoder3: MTL4ComputeCommandEncoder!
    computeEncoder3 = commandBuffer.makeComputeCommandEncoder()
    // Assign the argument table to the compute encoder.
    computeEncoder3.setArgumentTable(argumentTable)
    // Run a dispatch command that works with `bufferD`,
    // which the GPU runs during the dispatch stage.
    computeEncoder3.setComputePipelineState(modifyBufferIndex3ComputePipeline)
    computeEncoder3.dispatchThreadgroups(threadgroupsPerGrid: threadgroupCount,
                                         threadsPerThreadgroup: threadsPerThreadgroup)
    // Finalize the third compute pass.
    computeEncoder3.endEncoding()
}
```

```

```
    
```
// === Encode pass 3 ===
    // Create an encoder for the third compute pass.
    id<MTL4ComputeCommandEncoder> computeEncoder3;
    computeEncoder3 = [commandBuffer computeCommandEncoder];
    // Assign the argument table to the compute encoder.
    [computeEncoder3 setArgumentTable:argumentTable];
    // Run a dispatch command that works with `bufferD`,
    // which the GPU runs during the dispatch stage.
    [computeEncoder3 setComputePipelineState:modifyBufferIndex3ComputePipeline];
    [computeEncoder3 dispatchThreadgroups:threadgroupCount
                    threadsPerThreadgroup:threadsPerThreadgroup];
    // Finalize the third compute pass.
    [computeEncoder3 endEncoding];
}
```

```

The example has at least one access conflict because pass 2 and pass 3 both access the same communal resource, `bufferD`:

*   The copy command from the second pass stores to `bufferD`.
    
*   The dispatch command from the third pass loads from `bufferD`.
    

![](https://docs-assets.developer.apple.com/published/b8f2dddda491cfc8f09e6dc865f955c0/synchronizing-resource-accesses-with-subsequent-passes-with-a-producer-based-queue-barrier-1%402x.png)

Without synchronization, the GPU can run all three passes and their stages in parallel, which can yield inconsistent results in resources with access conflicts.

![](https://docs-assets.developer.apple.com/published/86e018ad27fa0e256bac86611e0224d2/synchronizing-resource-accesses-with-subsequent-passes-with-a-producer-based-queue-barrier-2%402x.png)

### [Resolve an intrapass conflict with a producer barrier](/documentation/Metal/synchronizing-resource-accesses-with-subsequent-passes-with-a-producer-based-queue-barrier#Resolve-an-intrapass-conflict-with-a-producer-barrier)

You can resolve access conflicts between passes from the same command queue with a producer barrier by calling the encoder’s [`barrier(afterStages:beforeQueueStages:visibilityOptions:)`](/documentation/metal/mtl4commandencoder/barrier\(afterstages:beforequeuestages:visibilityoptions:\)) method.

Each producer queue barrier temporarily blocks the GPU from running the specific stage types, which you pass to the `beforeQueueStages` parameter, from running in all subsequent passes in the same queue. The barrier unblocks the GPU from running those stages when all the stage types you pass to the `afterStages` parameter finish running in the current pass and all previous passes.

Important

The stages you pass to the `afterStages` parameter of the [`barrier(afterStages:beforeQueueStages:visibilityOptions:)`](/documentation/metal/mtl4commandencoder/barrier\(afterstages:beforequeuestages:visibilityoptions:\)) method apply to the current pass, but the stages you pass to the `beforeQueueStages` parameter don’t apply to the current pass.

The following example modifies the code that encodes the second pass by adding a producer queue barrier just before the dispatch command stage in the second pass.

    ```swift
    
```swift
// Copy from `bufferC` to `bufferD`, which runs during the blit stage.
    let bufferC = buffers[2]
    let bufferD = buffers[3]
    argumentTable.setAddress(bufferC.gpuAddress, index: 2)
    argumentTable.setAddress(bufferD.gpuAddress, index: 3)
    computeEncoder2.copy(sourceBuffer: bufferC, sourceOffset: 0,
                         destinationBuffer: bufferD, destinationOffset: 0,
                         size: copySize)
    // Add a producer queue barrier that blocks any dispatch stages in subsequent passes
    // in the queue, not counting this one, from running until the blit stages in all
    // previous passes finish running, including this one.
    computeEncoder2.barrier(afterStages: .blit,
                            beforeQueueStages: .dispatch,
                            visibilityOptions: .device)
    // Run a dispatch command that works with `bufferC`,
    // which the GPU runs during the dispatch stage.
    computeEncoder2.setComputePipelineState(modifyBufferIndex2ComputePipeline)
    computeEncoder2.dispatchThreadgroups(threadgroupsPerGrid: threadgroupCount,
                                         threadsPerThreadgroup: threadsPerThreadgroup)
    // Finalize the second compute pass.
    computeEncoder2.endEncoding()
```

```

```
    
```
// Copy from `bufferC` to `bufferD`, which runs during the blit stage.
    id<MTLBuffer> bufferC = buffers[2];
    id<MTLBuffer> bufferD = buffers[3];
    [argumentTable setAddress:bufferC.gpuAddress atIndex:2];
    [argumentTable setAddress:bufferD.gpuAddress atIndex:3];
    [computeEncoder2 copyFromBuffer:bufferC sourceOffset:0
                           toBuffer:bufferD destinationOffset:0
                               size:copySize];
    // Add a producer queue barrier that blocks any dispatch stages in subsequent passes
    // in the queue, not counting this one, from running until the blit stages in all
    // previous passes finish running, including this one.
    [computeEncoder2 barrierAfterStages:MTLStageBlit
                      beforeQueueStages:MTLStageDispatch
                      visibilityOptions:MTL4VisibilityOptionDevice];
    // Run a dispatch command that works with `bufferC`,
    // which the GPU runs during the dispatch stage.
    [computeEncoder2 setComputePipelineState:modifyBufferIndex2ComputePipeline];
    [computeEncoder2 dispatchThreadgroups:threadgroupCount
                    threadsPerThreadgroup:threadsPerThreadgroup];
    // Finalize the second compute pass.
    [computeEncoder2 endEncoding];
```

```

In this example, the barrier prevents the GPU from running the dispatch stage in the third pass until the blit stages in both the first and second pass finish storing their modifications.

![](https://docs-assets.developer.apple.com/published/899fbb275861abaa947f5dad152a6e28/synchronizing-resource-accesses-with-subsequent-passes-with-a-producer-based-queue-barrier-3%402x.png)

The barrier unblocks the dispatch stage of the third pass when the blit stage from the first pass finishes running because it’s the last blit stage to finish of all the passes that apply to the `afterStages` parameter.

## [See Also](/documentation/Metal/synchronizing-resource-accesses-with-subsequent-passes-with-a-producer-based-queue-barrier#see-also)

### [Synchronization](/documentation/Metal/synchronizing-resource-accesses-with-subsequent-passes-with-a-producer-based-queue-barrier#Synchronization)

[

Synchronizing resource accesses within a single pass with an intrapass barrier](/documentation/metal/synchronizing-resource-accesses-within-a-single-pass-with-an-intrapass-barrier)

Resolve resource access conflicts between stages within a single pass by adding an intrapass barrier.

[

Synchronizing resource accesses between multiple passes with a fence](/documentation/metal/synchronizing-resource-accesses-between-multiple-passes-with-a-fence)

Resolve resource access conflicts between multiple passes within a single command queue by signaling a fence in one pass and waiting for it in another.

[

Synchronizing resource accesses with earlier passes with a consumer-based queue barrier](/documentation/metal/synchronizing-resource-accesses-with-earlier-passes-with-a-consumer-based-queue-barrier)

Resolve resource access conflicts between multiple passes within a single command queue by creating a consumer-based intraqueue barrier.

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