

- Swift
- TaskGroup
-  isEmpty 

Instance Property

# isEmpty

A Boolean value that indicates whether the group has any remaining tasks.

iOS 13.0+iPadOS 13.0+Mac Catalyst 13.0+macOS 10.15+tvOS 13.0+visionOS 1.0+watchOS 6.0+

``` source
var isEmpty: Bool { get }
```

## Return Value

`true` if the group has no pending tasks; otherwise `false`.

## Discussion

At the start of the body of a `withTaskGroup(of:returning:body:)` call, the task group is always empty. It\`s guaranteed to be empty when returning from that body because a task group waits for all child tasks to complete before returning.

## See Also

### Accessing Individual Results

func next(isolation: isolated (any Actor)?) async -> ChildTaskResult?

Wait for the next child task to complete, and return the value it returned.

func waitForAll(isolation: isolated (any Actor)?) async

Wait for all of the group’s remaining tasks to complete.

