

- Swift
- ThrowingTaskGroup
-  next(isolation:) 

Instance Method

# next(isolation:)

Wait for the next child task to complete, and return the value it returned or rethrow the error it threw.

iOS 13.0+iPadOS 13.0+Mac Catalyst 13.0+macOS 10.15+tvOS 13.0+visionOS 1.0+watchOS 6.0+

``` source
@backDeployed(before: macOS 15.0, iOS 18.0, watchOS 11.0, tvOS 18.0, visionOS 2.0)
mutating func next(isolation: isolated (any Actor)? = #isolation) async throws -> ChildTaskResult?
```

## Return Value

The value returned by the next child task that completes.

## Discussion

The values returned by successive calls to this method appear in the order that the tasks *completed*, not in the order that those tasks were added to the task group. For example:

```
group.addTask { 1 }
group.addTask { 2 }

print(await group.next())
// Prints either "2" or "1".
```

If there aren’t any pending tasks in the task group, this method returns `nil`, which lets you write the following to wait for a single task to complete:

```
if let first = try await group.next() {
   return first
}
```

It also lets you write code like the following to wait for all the child tasks to complete, collecting the values they returned:

```
while let first = try await group.next() {
   collected += value
}
return collected
```

Awaiting on an empty group immediately returns `nil` without suspending.

You can also use a `for`-`await`-`in` loop to collect results of a task group:

```
for try await value in group {
    collected += value
}
```

If the next child task throws an error and you propagate that error from this method out of the body of a call to the `ThrowingTaskGroup.withThrowingTaskGroup(of:returning:body:)` method, then all remaining child tasks in that group are implicitly canceled.

Don’t call this method from outside the task where this task group was created. In most cases, the Swift type system prevents this mistake; for example, because the `add(priority:operation:)` method is mutating, that method can’t be called from a concurrent execution context like a child task.

Throws

The error thrown by the next child task that completes.

See Also

`nextResult()`

