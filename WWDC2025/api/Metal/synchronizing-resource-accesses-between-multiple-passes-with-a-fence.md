*   [Metal](/documentation/metal)
*   [Resource Synchronization](/documentation/metal/resource-synchronization)
*   Synchronizing resource accesses between multiple passes with a fence

Article

# Synchronizing resource accesses between multiple passes with a fence

Resolve resource access conflicts between multiple passes within a single command queue by signaling a fence in one pass and waiting for it in another.

## [Overview](/documentation/Metal/synchronizing-resource-accesses-between-multiple-passes-with-a-fence#overview)

A fence resolves access conflicts between commands in different passes that you submit to the same command queue, including the passes you commit in other command buffers.

Note

[`MTLFence`](/documentation/metal/mtlfence) instances in Metal 3 work across multiple command queues that belong to the same device; to synchronize across multiple command queues in Metal 4, instead use [`MTLEvent`](/documentation/metal/mtlevent) or [`MTLSharedEvent`](/documentation/metal/mtlsharedevent) instances.

Apps create an access conflict when they encode commands for different passes or different stages within a single pass that access the same resource, and at least one command that modifies a common resource. This conflict happens because the GPU can run multiple things at the same time, including:

*   Multiple passes
    
*   Different stages of a pass, such as the [`blit`](/documentation/metal/mtlstages/blit) and [`dispatch`](/documentation/metal/mtlstages/dispatch) stages of a compute pass
    
*   Multiple instances of a stage, such as two or more dispatch commands within a compute pass
    

For more information about resource access conflicts and GPU stages, see [Resource Synchronization](/documentation/metal/resource-synchronization) and [`MTLStages`](/documentation/metal/mtlstages), respectively.

Important

To synchronize stages within the same pass, you need to use an intrapass barrier instead of fence because fences can only synchronize between stages of different passes.

For more information about synchronizing within a single pass, see [Synchronizing resource accesses within a single pass with an intrapass barrier](/documentation/metal/synchronizing-resource-accesses-within-a-single-pass-with-an-intrapass-barrier).

Start by identifying which accesses from different passes introduce a conflict and resolve it by:

1.  Updating that fence in the producing pass
    
2.  Waiting for a fence in the consuming pass
    

### [Identify an access conflict between two or more passes on a single queue](/documentation/Metal/synchronizing-resource-accesses-between-multiple-passes-with-a-fence#Identify-an-access-conflict-between-two-or-more-passes-on-a-single-queue)

The following code example encodes two compute passes. The first encoder creates a pass with a copy command and a dispatch command:

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
func encodeComputeWorkWithFence(fence: MTLFence,
```
```
                                commandBuffer: MTL4CommandBuffer,
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
    // Copy from `bufferA` to `bufferB`, which runs during the blit stage.
    computeEncoder1.copy(sourceBuffer: bufferA, sourceOffset: 0,
                        destinationBuffer: bufferB, destinationOffset: 0,
                        size: copySize)
    // Run a dispatch command that modifies `bufferC`,
    // which the GPU runs during the dispatch stage.
    let bufferC = buffers[2]
    argumentTable.setAddress(bufferC.gpuAddress, index: 2)
    computeEncoder1.setComputePipelineState(modifyBufferIndex2ComputePipeline)
    computeEncoder1.dispatchThreadgroups(threadgroupsPerGrid: threadgroupCount,
                                         threadsPerThreadgroup: threadsPerThreadgroup)
    // Pass 1 needs to update a fence here.
    // Finalize the first compute pass.
    computeEncoder1.endEncoding()
```
```
```
```
```

```

```
- (void)encodeComputeWorkWithFence:(id<MTLFence>)fence
                     commandBuffer:(id<MTL4CommandBuffer>)commandBuffer
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
    // Run a dispatch command that modifies `bufferC`,
    // which the GPU runs during the dispatch stage.
    id<MTLBuffer> bufferC = buffers[2];
    [argumentTable setAddress:bufferC.gpuAddress atIndex:2];
    [computeEncoder1 setComputePipelineState:modifyBufferIndex2ComputePipeline];
    [computeEncoder1 dispatchThreadgroups:threadgroupCount
                    threadsPerThreadgroup:threadsPerThreadgroup];
    // Pass 1 needs to update a fence here.
    // Finalize the first compute pass.
    [computeEncoder1 endEncoding];
```

```
```
```
```
```

The second encoder also creates a pass with a copy command and a dispatch command:

    ```swift
    
```swift
// === Encode pass 2 ===
    // Create an encoder for the second compute pass.
    let computeEncoder2: MTL4ComputeCommandEncoder!
    computeEncoder2 = commandBuffer.makeComputeCommandEncoder()
    // Assign the argument table to the compute encoder.
    computeEncoder2.setArgumentTable(argumentTable)
    // Pass 2 needs to wait for a fence here.
    // Copy from `bufferC` to `bufferD`, which runs during the blit stage.
    let bufferD = buffers[3]
    argumentTable.setAddress(bufferD.gpuAddress, index: 3)
    computeEncoder2.copy(sourceBuffer: bufferC, sourceOffset: 0,
                         destinationBuffer: bufferD, destinationOffset: 0,
                         size: copySize)
    // Run a dispatch command that works with `bufferE`.
    let bufferE = buffers[4]
    argumentTable.setAddress(bufferE.gpuAddress, index: 4)
    computeEncoder2.setComputePipelineState(modifyBufferIndex4ComputePipeline)
    computeEncoder2.dispatchThreadgroups(threadgroupsPerGrid: threadgroupCount,
                                         threadsPerThreadgroup: threadsPerThreadgroup)
    // Finalize the second compute pass.
    computeEncoder2.endEncoding()
}
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
    // Pass 2 needs to wait for a fence here.
    // Copy from `bufferC` to `bufferD`, which runs during the blit stage.
    id<MTLBuffer> bufferD = buffers[3];
    [argumentTable setAddress:bufferD.gpuAddress atIndex:3];
    [computeEncoder2 copyFromBuffer:bufferC sourceOffset:0
                           toBuffer:bufferD destinationOffset:0
                               size:copySize];
    // Run a dispatch command that works with `bufferE`.
    id<MTLBuffer> bufferE = buffers[4];
    [argumentTable setAddress:bufferE.gpuAddress atIndex:4];
    [computeEncoder2 setComputePipelineState:modifyBufferIndex4ComputePipeline];
    [computeEncoder2 dispatchThreadgroups:threadgroupCount
                    threadsPerThreadgroup:threadsPerThreadgroup];
    // Finalize the second compute pass.
    [computeEncoder2 endEncoding];
}
```

```

The example has at least one access conflict because both passes access the same communal resource, `bufferC`:

*   The dispatch command from the first pass stores to `bufferC`.
    
*   The copy command from the second pass loads from `bufferC`.
    

![](https://docs-assets.developer.apple.com/published/28d5ebee107bbb409190cbb05e26c1ed/synchronizing-resource-accesses-between-multiple-passes-with-a-fence-1%402x.png)

Without synchronization, the GPU can run both passes and their stages in parallel, which can yield inconsistent results in resources with access conflicts.

![](https://docs-assets.developer.apple.com/published/65040b6893724b010f8e5ba720284e78/synchronizing-resource-accesses-between-multiple-passes-with-a-fence-2%402x.png)

### [Resolve an inter-pass conflict with a fence](/documentation/Metal/synchronizing-resource-accesses-between-multiple-passes-with-a-fence#Resolve-an-inter-pass-conflict-with-a-fence)

You can resolve access conflicts between passes from the same command queue with an [`MTLFence`](/documentation/metal/mtlfence) instance by:

*   Instructing the producing pass to signal to the other pass that it’s done by calling the encoder’s [`updateFence(_:afterEncoderStages:)`](/documentation/metal/mtl4commandencoder/updatefence\(_:afterencoderstages:\)) method.
    
*   Instructing the consuming pass to wait for the fence by calling the encoder’s [`waitForFence(_:beforeEncoderStages:)`](/documentation/metal/mtl4commandencoder/waitforfence\(_:beforeencoderstages:\)) method.
    

The GPU pauses before running the commands you encode in the consuming pass after the wait command until the GPU runs _every_ update command you encode for the same fence in all the other relevant, producing passes.

Tip

To get the best runtime performance in passes that update or wait for a fence, encode them as close as possible to the commands that introduce resource access conflicts.

The following code example modifies the code for the first pass by adding a call that updates the fence:

    ```swift
    
```swift
// Run a dispatch command that modifies `bufferC`,
    // which the GPU runs during the dispatch stage.
    let bufferC = buffers[2]
    argumentTable.setAddress(bufferC.gpuAddress, index: 2)
    computeEncoder1.setComputePipelineState(modifyBufferIndex2ComputePipeline)
    computeEncoder1.dispatchThreadgroups(threadgroupsPerGrid: threadgroupCount,
                                         threadsPerThreadgroup: threadsPerThreadgroup)
    // Unblock the pass 2 that's waiting on the fence by
    // updating it when the dispatch stage (of pass 1) is done.
    computeEncoder1.updateFence(fence, afterEncoderStages: .dispatch)
    // Finalize the first compute pass.
    computeEncoder1.endEncoding()
```

```

```
    
```
// Run a dispatch command that modifies `bufferC`,
    // which the GPU runs during the dispatch stage.
    id<MTLBuffer> bufferC = buffers[2];
    [argumentTable setAddress:bufferC.gpuAddress atIndex:2];
    [computeEncoder1 setComputePipelineState:modifyBufferIndex2ComputePipeline];
    [computeEncoder1 dispatchThreadgroups:threadgroupCount
                    threadsPerThreadgroup:threadsPerThreadgroup];
    // Unblock the pass 2 that's waiting on the fence by
    // updating it when the dispatch stage (of pass 1) is done.
    [computeEncoder1 updateFence:fence afterEncoderStages:MTLStageDispatch];
    // Finalize the first compute pass.
    [computeEncoder1 endEncoding];
```

```

The following code example modifies the code for the second pass by adding a call that waits for the fence.

    ```swift
    
```swift
// Assign the argument table to the compute encoder.
    computeEncoder2.setArgumentTable(argumentTable)
    // Wait for pass 1 to update the fence.
    computeEncoder2.waitForFence(fence, beforeEncoderStages: .blit)
    // Copy from `bufferC` to `bufferD`, which runs during the blit stage.
    let bufferD = buffers[3]
    argumentTable.setAddress(bufferD.gpuAddress, index: 3)
    computeEncoder2.copy(sourceBuffer: bufferC, sourceOffset: 0,
                         destinationBuffer: bufferD, destinationOffset: 0,
                         size: copySize)
```

```

```
    
```
// Assign the argument table to the compute encoder.
    [computeEncoder2 setArgumentTable:argumentTable];
    // Wait for pass 1 to update the fence.
    [computeEncoder2 waitForFence:fence beforeEncoderStages:MTLStageBlit];
    // Copy from `bufferC` to `bufferD`, which runs during the blit stage.
    id<MTLBuffer> bufferD = buffers[3];
    [argumentTable setAddress:bufferD.gpuAddress atIndex:3];
    [computeEncoder2 copyFromBuffer:bufferC sourceOffset:0
                           toBuffer:bufferD destinationOffset:0
                               size:copySize];
```

```

The fence forces the GPU to wait before it runs the blit stage of the second pass until the dispatch stage of the first pass finishes storing its modifications to the underlying memory for `bufferC`.

![](https://docs-assets.developer.apple.com/published/7d54c4f8d610a94a846e38d6536472c8/synchronizing-resource-accesses-between-multiple-passes-with-a-fence-3%402x.png)

You can reuse a fence instance to resolve resource access conflicts in subsequent commands after encoding a wait command for a pass.

Important

To reuse a fence within the same pass, you need to encode the wait command first and then encode the update command.

## [See Also](/documentation/Metal/synchronizing-resource-accesses-between-multiple-passes-with-a-fence#see-also)

### [Synchronization](/documentation/Metal/synchronizing-resource-accesses-between-multiple-passes-with-a-fence#Synchronization)

[

Synchronizing resource accesses within a single pass with an intrapass barrier](/documentation/metal/synchronizing-resource-accesses-within-a-single-pass-with-an-intrapass-barrier)

Resolve resource access conflicts between stages within a single pass by adding an intrapass barrier.

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