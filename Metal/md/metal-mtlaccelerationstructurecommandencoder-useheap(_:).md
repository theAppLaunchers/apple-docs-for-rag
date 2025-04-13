

- Metal
- MTLAccelerationStructureCommandEncoder
-  useHeap(\_:) 

Instance Method

# useHeap(\_:)

Makes the resources contained in the specified heap available to the acceleration structure pass.

iOS 14.0+iPadOS 14.0+Mac Catalyst 14.0+macOS 11.0+tvOS 16.0+visionOS 1.0+

``` source
func useHeap(_ heap: any MTLHeap)
```

**Required**

## Parameters 

`heap`  

A heap that contains resources within an argument buffer.

## Discussion

This method makes all the resources in the heap resident for the duration of a compute pass and ensures that they’re in a format compatible with the compute function.

Call this method before issuing any dispatch calls that may access the resources in the heap.

You can only read or sample resources in the specified heap. This method ignores render targets (textures that specify a renderTarget usage option) and writable textures (textures that specify a shaderWrite usage option) within the heap. To use these resources, you must call the useResource(_:usage:) method instead.

Note

To track resource access and dependency hazards, you must use MTLFence objects.

## See Also

### Specifying Resource Usage for Argument Buffers

func useHeaps([any MTLHeap])

Makes the resources contained in the specified heaps available to the acceleration structure pass.

func useResource(any MTLResource, usage: MTLResourceUsage)

Makes a resource available to the acceleration structure pass.

**Required**

func useResources([any MTLResource], usage: MTLResourceUsage)

Makes multiple resources available to the acceleration structure pass.

struct MTLResourceUsage

Options that describe how a graphics or compute function uses an argument buffer’s resource.

