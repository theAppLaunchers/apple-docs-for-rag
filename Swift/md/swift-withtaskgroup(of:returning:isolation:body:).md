

- Swift
-  withTaskGroup(of:returning:isolation:body:) 

Function

# withTaskGroup(of:returning:isolation:body:)

Starts a new scope that can contain a dynamic number of child tasks.

iOS 13.0+iPadOS 13.0+Mac Catalyst 13.0+macOS 10.15+tvOS 13.0+visionOS 1.0+watchOS 6.0+

``` source
@backDeployed(before: macOS 15.0, iOS 18.0, watchOS 11.0, tvOS 18.0, visionOS 2.0)
func withTaskGroup(
    of childTaskResultType: ChildTaskResult.Type = ChildTaskResult.self,
    returning returnType: GroupResult.Type = GroupResult.self,
    isolation: isolated (any Actor)? = #isolation,
    body: (inout TaskGroup) async -> GroupResult
) async -> GroupResult where ChildTaskResult : Sendable
```

## Discussion

A group waits for all of its child tasks to complete or be canceled before it returns. After this function returns, the task group is always empty.

To collect the results of the group’s child tasks, you can use a `for`-`await`-`in` loop:

```
var sum = 0
for await result in group {
    sum += result
}
```

If you need more control or only a few results, you can call `next()` directly:

```
guard let first = await group.next() else {
    group.cancelAll()
    return 0
}
let second = await group.next() ?? 0
group.cancelAll()
return first + second
```

# Task Group Cancellation

You can cancel a task group and all of its child tasks by calling the `cancelAll()` method on the task group, or by canceling the task in which the group is running.

If you call `addTask(priority:operation:)` to create a new task in a canceled group, that task is immediately canceled after creation. Alternatively, you can call `addTaskUnlessCancelled(priority:operation:)`, which doesn’t create the task if the group has already been canceled. Choosing between these two functions lets you control how to react to cancellation within a group: some child tasks need to run regardless of cancellation, but other tasks are better not even being created when you know they can’t produce useful results.

Because the tasks you add to a group with this method are nonthrowing, those tasks can’t respond to cancellation by throwing `CancellationError`. The tasks must handle cancellation in some other way, such as returning the work completed so far, returning an empty result, or returning `nil`. For tasks that need to handle cancellation by throwing an error, use the `withThrowingTaskGroup(of:returning:body:)` method instead.

## See Also

### Tasks

struct Task

A unit of asynchronous work.

struct TaskGroup

A group that contains dynamically created child tasks.

struct ThrowingTaskGroup

A group that contains throwing, dynamically created child tasks.

func withThrowingTaskGroup&lt;ChildTaskResult, GroupResult>(of: ChildTaskResult.Type, returning: GroupResult.Type, isolation: isolated (any Actor)?, body: (inout ThrowingTaskGroup&lt;ChildTaskResult, any Error>) async throws -> GroupResult) async rethrows -> GroupResult

Starts a new scope that can contain a dynamic number of throwing child tasks.

struct TaskPriority

The priority of a task.

struct DiscardingTaskGroup

A discarding group that contains dynamically created child tasks.

func withDiscardingTaskGroup&lt;GroupResult>(returning: GroupResult.Type, isolation: isolated (any Actor)?, body: (inout DiscardingTaskGroup) async -> GroupResult) async -> GroupResult

Starts a new scope that can contain a dynamic number of child tasks.

struct ThrowingDiscardingTaskGroup

A throwing discarding group that contains dynamically created child tasks.

func withThrowingDiscardingTaskGroup&lt;GroupResult>(returning: GroupResult.Type, isolation: isolated (any Actor)?, body: (inout ThrowingDiscardingTaskGroup&lt;any Error>) async throws -> GroupResult) async throws -> GroupResult

Starts a new scope that can contain a dynamic number of child tasks.

struct UnsafeCurrentTask

An unsafe reference to the current task.

