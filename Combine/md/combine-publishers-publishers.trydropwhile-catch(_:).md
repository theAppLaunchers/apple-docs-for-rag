

- Combine
- Publishers
- Publishers.TryDropWhile
-  catch(\_:) 

Instance Method

# catch(\_:)

Handles errors from an upstream publisher by replacing it with another publisher.

iOS 13.0+iPadOS 13.0+Mac Catalyst 13.0+macOS 10.15+tvOS 13.0+visionOS 1.0+watchOS 6.0+

``` source
func `catch`(_ handler: @escaping (Self.Failure) -> P) -> Publishers.Catch where P : Publisher, Self.Output == P.Output
```

## Parameters 

`handler`  

A closure that accepts the upstream failure as input and returns a publisher to replace the upstream publisher.

## Return Value

A publisher that handles errors from an upstream publisher by replacing the failed publisher with another publisher.

## Discussion

Use `catch()` to replace an error from an upstream publisher with a new publisher.

In the example below, the `catch()` operator handles the `SimpleError` thrown by the upstream publisher by replacing the error with a `Just` publisher. This continues the stream by publishing a single value and completing normally.

```
struct SimpleError: Error {}
let numbers = [5, 4, 3, 2, 1, 0, 9, 8, 7, 6]
cancellable = numbers.publisher
    .tryLast(where: {
        guard $0 != 0 else {throw SimpleError()}
        return true
    })
    .catch({ (error) in
        Just(-1)
    })
    .sink { print("\($0)") }
    // Prints: -1
```

Backpressure note: This publisher passes through `request` and `cancel` to the upstream. After receiving an error, the publisher sends sends any unfulfilled demand to the new `Publisher`. SeeAlso: `replaceError`

## See Also

### Handling Errors

func assertNoFailure(String, file: StaticString, line: UInt) -> Publishers.AssertNoFailure&lt;Self>

Raises a fatal error when its upstream publisher fails, and otherwise republishes all received input.

func tryCatch&lt;P>((Self.Failure) throws -> P) -> Publishers.TryCatch&lt;Self, P>

Handles errors from an upstream publisher by either replacing it with another publisher or throwing a new error.

func retry(Int) -> Publishers.Retry&lt;Self>

Attempts to recreate a failed subscription with the upstream publisher up to the number of times you specify.

