

- Combine
- Publishers
- Publishers.TryLastWhere
-  tryCatch(\_:) 

Instance Method

# tryCatch(\_:)

Handles errors from an upstream publisher by either replacing it with another publisher or throwing a new error.

iOS 13.0+iPadOS 13.0+Mac Catalyst 13.0+macOS 10.15+tvOS 13.0+visionOS 1.0+watchOS 6.0+

``` source
func tryCatch(_ handler: @escaping (Self.Failure) throws -> P) -> Publishers.TryCatch where P : Publisher, Self.Output == P.Output
```

## Parameters 

`handler`  

A throwing closure that accepts the upstream failure as input. This closure can either replace the upstream publisher with a new one, or throw a new error to the downstream subscriber.

## Return Value

A publisher that handles errors from an upstream publisher by replacing the failed publisher with another publisher, or an error.

## Discussion

Use tryCatch(_:) to decide how to handle from an upstream publisher by either replacing the publisher with a new publisher, or throwing a new error.

In the example below, an array publisher emits values that a tryMap(_:) operator evaluates to ensure the values are greater than zero. If the values aren’t greater than zero, the operator throws an error to the downstream subscriber to let it know there was a problem. The subscriber, tryCatch(_:), replaces the error with a new publisher using Just to publish a final value before the stream ends normally.

```
enum SimpleError: Error { case error }
var numbers = [5, 4, 3, 2, 1, -1, 7, 8, 9, 10]

cancellable = numbers.publisher
   .tryMap { v in
        if v > 0 {
            return v
        } else {
            throw SimpleError.error
        }
}
  .tryCatch { error in
      Just(0) // Send a final value before completing normally.
              // Alternatively, throw a new error to terminate the stream.
}
  .sink(receiveCompletion: { print ("Completion: \($0).") },
        receiveValue: { print ("Received \($0).") }
  )
//    Received 5.
//    Received 4.
//    Received 3.
//    Received 2.
//    Received 1.
//    Received 0.
//    Completion: finished.
```

## See Also

### Handling Errors

func assertNoFailure(String, file: StaticString, line: UInt) -> Publishers.AssertNoFailure&lt;Self>

Raises a fatal error when its upstream publisher fails, and otherwise republishes all received input.

func `catch`&lt;P>((Self.Failure) -> P) -> Publishers.Catch&lt;Self, P>

Handles errors from an upstream publisher by replacing it with another publisher.

func retry(Int) -> Publishers.Retry&lt;Self>

Attempts to recreate a failed subscription with the upstream publisher up to the number of times you specify.

