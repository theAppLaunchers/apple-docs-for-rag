

- Swift
- StrideThrough
-  drop(while:) 

Instance Method

# drop(while:)

Returns a sequence by skipping the initial, consecutive elements that satisfy the given predicate.

iOS 8.0+iPadOS 8.0+Mac Catalyst 13.0+macOS 10.10+tvOS 9.0+visionOS 1.0+watchOS 2.0+

``` source
func drop(while predicate: (Self.Element) throws -> Bool) rethrows -> DropWhileSequence
```

## Parameters 

`predicate`  

A closure that takes an element of the sequence as its argument and returns a Boolean value indicating whether the element should be included in the result.

## Return Value

A sequence starting after the initial, consecutive elements that satisfy `predicate`.

## Discussion

The following example uses the `drop(while:)` method to skip over the positive numbers at the beginning of the `numbers` array. The result begins with the first element of `numbers` that does not satisfy `predicate`.

```
let numbers = [3, 7, 4, -2, 9, -6, 10, 1]
let startingWithNegative = numbers.drop(while: { $0 > 0 })
// startingWithNegative == [-2, 9, -6, 10, 1]
```

If `predicate` matches every element in the sequence, the result is an empty sequence.

Complexity

O(*k*), where *k* is the number of elements to drop from the beginning of the sequence.

