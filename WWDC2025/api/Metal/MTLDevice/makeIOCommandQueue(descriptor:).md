*   [Metal](/documentation/metal)
*   [MTLDevice](/documentation/metal/mtldevice)
*   makeIOCommandQueue(descriptor:)

Instance Method

# makeIOCommandQueue(descriptor:)

Creates an input/output command queue you use to submit commands that load assets from the file system into GPU resources or system memory.

iOS 16.0+iPadOS 16.0+Mac Catalyst 16.0+macOS 13.0+tvOS 16.0+visionOS 1.0+

```swift
```swift
```swift
```swift
```swift
```swift
```swift
```swift
func makeIOCommandQueue(descriptor: [`MTLIOCommandQueueDescriptor`](/documentation/metal/mtliocommandqueuedescriptor)) throws -> any [`MTLIOCommandQueue`](/documentation/metal/mtliocommandqueue)
```
```
```
```
```
```
```
```

**Required**

## [Parameters](/documentation/Metal/MTLDevice/makeIOCommandQueue\(descriptor:\)#parameters)

`descriptor`

A descriptor instance that configures the command queue.

## [Return Value](/documentation/Metal/MTLDevice/makeIOCommandQueue\(descriptor:\)#return-value)

A new [`MTLIOCommandQueue`](/documentation/metal/mtliocommandqueue) instance if the method completes successfully; otherwise Swift throws an error and Objective-C returns `nil`.

## [Discussion](/documentation/Metal/MTLDevice/makeIOCommandQueue\(descriptor:\)#discussion)

For information about using input/output command queues and file handles, see [Resource Loading](/documentation/metal/resource-loading).