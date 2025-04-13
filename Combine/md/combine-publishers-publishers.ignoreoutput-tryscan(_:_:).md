

- Combine
- Publishers
- Publishers.IgnoreOutput
-  tryScan(\_:\_:) 

Instance Method

# tryScan(\_:\_:)

Transforms elements from the upstream publisher by providing the current element to an error-throwing closure along with the last value returned by the closure.

iOS 13.0+iPadOS 13.0+Mac Catalyst 13.0+macOS 10.15+tvOS 13.0+visionOS 1.0+watchOS 6.0+

``` source
func tryScan(
    _ initialResult: T,
    _ nextPartialResult: @escaping (T, Self.Output) throws -> T
) -> Publishers.TryScan
```

## Parameters 

`initialResult`  

The previous result returned by the `nextPartialResult` closure.

`nextPartialResult`  

An error-throwing closure that takes as its arguments the previous value returned by the closure and the next element emitted from the upstream publisher.

## Return Value

A publisher that transforms elements by applying a closure that receives its previous return value and the next element from the upstream publisher.

## Discussion

Use tryScan(_:_:) to accumulate all previously-published values into a single value, which you then combine with each newly-published value. If your accumulator closure throws an error, the publisher terminates with the error.

In the example below, tryScan(_:_:) calls a division function on elements of a collection publisher. The Publishers.TryScan publisher publishes each result until the function encounters a `DivisionByZeroError`, which terminates the publisher.

```
struct DivisionByZeroError: Error {}

/// A function that throws a DivisionByZeroError if `current` provided by the TryScan publisher is zero.
func myThrowingFunction(_ lastValue: Int, _ currentValue: Int) throws -> Int {
    guard currentValue != 0 else { throw DivisionByZeroError() }
    return (lastValue + currentValue) / currentValue
 }

let numbers = [1,2,3,4,5,0,6,7,8,9]
cancellable = numbers.publisher
    .tryScan(10) { try myThrowingFunction($0, $1) }
    .sink(
        receiveCompletion: { print ("\($0)") },
        receiveValue: { print ("\($0)", terminator: " ") }
     )

// Prints: "11 6 3 1 1 -1 failure(DivisionByZeroError())".
```

If the closure throws an error, the publisher fails with the error.

## See Also

### Mapping Elements

func map&lt;T>((Self.Output) -> T) -> Publishers.Map&lt;Self, T>

Transforms all elements from the upstream publisher with a provided closure.

func tryMap&lt;T>((Self.Output) throws -> T) -> Publishers.TryMap&lt;Self, T>

Transforms all elements from the upstream publisher with a provided error-throwing closure.

func mapError&lt;E>((Self.Failure) -> E) -> Publishers.MapError&lt;Self, E>

Converts any failure from the upstream publisher into a new error.

func replaceNil&lt;T>(with: T) -> Publishers.Map&lt;Self, T>

Replaces nil elements in the stream with the provided element.

func scan&lt;T>(T, (T, Self.Output) -> T) -> Publishers.Scan&lt;Self, T>

Transforms elements from the upstream publisher by providing the current element to a closure along with the last value returned by the closure.

func setFailureType&lt;E>(to: E.Type) -> Publishers.SetFailureType&lt;Self, E>

Changes the failure type declared by the upstream publisher.

