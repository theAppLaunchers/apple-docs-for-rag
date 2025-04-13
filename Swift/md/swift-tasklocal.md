

- Swift
-  TaskLocal 

Class

# TaskLocal

Wrapper type that defines a task-local value key.

iOS 13.0+iPadOS 13.0+Mac Catalyst 13.0+macOS 10.15+tvOS 13.0+visionOS 1.0+watchOS 6.0+

``` source
final class TaskLocal where Value : Sendable
```

## Overview

A task-local value is a value that can be bound and read in the context of a Task. It is implicitly carried with the task, and is accessible by any child tasks it creates (such as TaskGroup or `async let` created tasks).

### Task-local declarations

Task locals must be declared as static properties or global properties, like this:

```
enum Example {
    @TaskLocal
    static var traceID: TraceID?
}

// Global task local properties are supported since Swift 6.0:
@TaskLocal
var contextualNumber: Int = 12
```

### Default values

Reading a task local value when no value was bound to it results in returning its default value. For a task local declared as optional (such as e.g. `TraceID?`), this defaults to nil, however a different default value may be defined at declaration site of the task local, like this:

```
enum Example { 
    @TaskLocal
    static var traceID: TraceID = TraceID.default
}
```

The default value is returned whenever the task-local is read from a context which either: has no task available to read the value from (e.g. a synchronous function, called without any asynchronous function in its call stack), or no value was bound within the scope of the current task or any of its parent tasks.

### Reading task-local values

Reading task local values is simple and looks the same as-if reading a normal static property:

```
guard let traceID = Example.traceID else {
  print("no trace id")
  return
}
print(traceID)
```

It is possible to perform task-local value reads from either asynchronous or synchronous functions.

### Binding task-local values

Task local values cannot be `set` directly and must instead be bound using the scoped `$traceID.withValue() { ... }` operation. The value is only bound for the duration of that scope, and is available to any child tasks which are created within that scope.

Detached tasks do not inherit task-local values, however tasks created using the `Task { ... }` initializer do inherit task-locals by copying them to the new asynchronous task, even though it is an un-structured task.

### Using task local values outside of tasks

It is possible to bind and read task local values outside of tasks.

This comes in handy within synchronous functions which are not guaranteed to be called from within a task. When binding a task-local value from outside of a task, the runtime will set a thread-local in which the same storage mechanism as used within tasks will be used. This means that you can reliably bind and read task local values without having to worry about the specific calling context, e.g.:

```
func enter() {
    Example.$traceID.withValue("1234") {
        read() // always "1234", regardless if enter() was called from inside a task or not:
}

func read() -> String {
    if let value = Self.traceID {
        "\(value)" 
    } else { 
        ""
    }
}

// 1) Call `enter` from non-Task code
//    e.g. synchronous main() or non-Task thread (e.g. a plain pthread)
enter()

// 2) Call 'enter' from Task
Task { 
    enter()
}
```

In either cases listed above, the binding and reading of the task-local value works as expected.

### Examples

```
enum Example {
    @TaskLocal
    static var traceID: TraceID?
}

func read() -> String {
    if let value = Self.traceID {
        "\(value)" 
    } else { 
        ""
    }
}

await Example.$traceID.withValue(1234) { // bind the value
  print("traceID: \(Example.traceID)") // traceID: 1234
  read() // traceID: 1234

  async let id = read() // async let child task, traceID: 1234

  await withTaskGroup(of: String.self) { group in 
      group.addTask { read() } // task group child task, traceID: 1234
      return await group.next()!
  }

  Task { // unstructured tasks do inherit task locals by copying
    read() // traceID: 1234
  }

  Task.detached { // detached tasks do not inherit task-local values
    read() // traceID: nil
  }
}
```

See Also

`TaskLocal-macro`

## Topics

### Initializers

init(wrappedValue: Value)

### Instance Properties

var description: String

A textual representation of this instance.

var projectedValue: TaskLocal&lt;Value>

var wrappedValue: Value

### Instance Methods

func get() -> Value

Gets the value currently bound to this task-local from the current task.

func withValue&lt;R>(Value, operation: () throws -> R, file: String, line: UInt) rethrows -> R

Binds the task-local to the specific value for the duration of the synchronous operation.

func withValue&lt;R>(Value, operation: () async throws -> R, isolation: isolated (any Actor)?, file: String, line: UInt) async rethrows -> R

Binds the task-local to the specific value for the duration of the asynchronous operation.

## Relationships

### Conforms To

- CustomStringConvertible
- Sendable

## See Also

### Task-Local Storage

macro TaskLocal()

Macro that introduces a TaskLocal binding.

