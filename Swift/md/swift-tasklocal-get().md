

- Swift
- TaskLocal
-  get() 

Instance Method

# get()

Gets the value currently bound to this task-local from the current task.

iOS 13.0+iPadOS 13.0+Mac Catalyst 13.0+macOS 10.15+tvOS 13.0+visionOS 1.0+watchOS 6.0+

``` source
final func get() -> Value
```

## Discussion

If no current task is available in the context where this call is made, or if the task-local has no value bound, this will return the `defaultValue` of the task local.

