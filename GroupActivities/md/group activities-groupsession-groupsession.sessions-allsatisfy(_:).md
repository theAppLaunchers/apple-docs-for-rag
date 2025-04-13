

- Group Activities
- GroupSession
- GroupSession.Sessions
-  allSatisfy(\_:) 

Instance Method

# allSatisfy(\_:)

Returns a Boolean value that indicates whether all elements produced by the asynchronous sequence satisfy the given predicate.

Group ActivitiesSwiftiOS 13.0+iPadOS 13.0+Mac Catalyst 13.0+macOS 10.15+tvOS 13.0+visionOS 1.0+watchOS 6.0+

``` source
func allSatisfy(_ predicate: (Self.Element) async throws -> Bool) async rethrows -> Bool
```

## Parameters 

`predicate`  

A closure that takes an element of the asynchronous sequence as its argument and returns a Boolean value that indicates whether the passed element satisfies a condition.

## Return Value

`true` if the sequence contains only elements that satisfy `predicate`; otherwise, `false`.

## Discussion

In this example, an asynchronous sequence called `Counter` produces `Int` values from `1` to `10`. The `allSatisfy(_:)` method checks to see whether all elements produced by the sequence are less than `10`.

```
let allLessThanTen = await Counter(howHigh: 10)
    .allSatisfy { $0 

The predicate executes each time the asynchronous sequence produces an element, until either the predicate returns `false` or the sequence ends.

If the asynchronous sequence is empty, this method returns `true`.

## See Also

### Finding elements

func contains(where: (Self.Element) async throws -> Bool) async rethrows -> Bool

Returns a Boolean value that indicates whether the asynchronous sequence contains an element that satisfies the given predicate.

func first(where: (Self.Element) async throws -> Bool) async rethrows -> Self.Element?

Returns the first element of the sequence that satisfies the given predicate.

func min(by: (Self.Element, Self.Element) async throws -> Bool) async rethrows -> Self.Element?

Returns the minimum element in the asynchronous sequence, using the given predicate as the comparison between elements.

func max(by: (Self.Element, Self.Element) async throws -> Bool) async rethrows -> Self.Element?

Returns the maximum element in the asynchronous sequence, using the given predicate as the comparison between elements.

