

- Swift
- ThrowingTaskGroup
- ThrowingTaskGroup.Iterator
-  next(isolation:) 

Instance Method

# next(isolation:)

Advances to and returns the result of the next child task.

iOS 18.0+iPadOS 18.0+Mac Catalyst 18.0+macOS 15.0+tvOS 18.0+visionOS 2.0+watchOS 11.0+

``` source
mutating func next(isolation actor: isolated (any Actor)?) async throws(Failure) -> ThrowingTaskGroup.Iterator.Element?
```

## Return Value

The value returned by the next child task that completes, or `nil` if there are no remaining child tasks,

## Discussion

The elements returned from this method appear in the order that the tasks *completed*, not in the order that those tasks were added to the task group. After this method returns `nil`, this iterator is guaranteed to never produce more values.

For more information about the iteration order and semantics, see `ThrowingTaskGroup.next()`

Throws

The error thrown by the next child task that completes.

