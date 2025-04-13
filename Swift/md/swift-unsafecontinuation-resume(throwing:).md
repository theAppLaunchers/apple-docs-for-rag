

- Swift
- UnsafeContinuation
-  resume(throwing:) 

Instance Method

# resume(throwing:)

Resume the task that’s awaiting the continuation by throwing the given error.

iOS 13.0+iPadOS 13.0+Mac Catalyst 13.0+macOS 10.15+tvOS 13.0+visionOS 1.0+watchOS 6.0+

``` source
func resume(throwing error: consuming E)
```

## Parameters 

`error`  

The error to throw from the continuation.

## Discussion

A continuation must be resumed exactly once. If the continuation has already resumed, then calling this method results in undefined behavior.

After calling this method, control immediately returns to the caller. The task continues executing when its executor schedules it.

