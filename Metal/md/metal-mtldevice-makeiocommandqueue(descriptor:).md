

- Metal
- MTLDevice
-  makeIOCommandQueue(descriptor:) 

Instance Method

# makeIOCommandQueue(descriptor:)

Creates an input/output command queue you use to submit commands that load assets from the file system into GPU resources or system memory.

iOS 16.0+iPadOS 16.0+Mac Catalyst 16.0+macOS 13.0+tvOS 16.0+visionOS 1.0+

``` source
func makeIOCommandQueue(descriptor: MTLIOCommandQueueDescriptor) throws -> any MTLIOCommandQueue
```

**Required**

## Parameters 

`descriptor`  

A descriptor instance that configures the command queue.

## Return Value

A new MTLIOCommandQueue instance if the method completes successfully; otherwise Swift throws an error and Objective-C returns `nil`.

## Discussion

For information about using input/output command queues and file handles, see Resource Loading.

