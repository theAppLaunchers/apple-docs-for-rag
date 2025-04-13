

- Swift
- Array
-  removeAll(where:) 

Instance Method

# removeAll(where:)

Removes all the elements that satisfy the given predicate.

iOS 8.0+iPadOS 8.0+Mac Catalyst 13.0+macOS 10.10+tvOS 9.0+visionOS 1.0+watchOS 2.0+

``` source
mutating func removeAll(where shouldBeRemoved: (Self.Element) throws -> Bool) rethrows
```

Available when `Self` conforms to `MutableCollection`.

## Parameters 

`shouldBeRemoved`  

A closure that takes an element of the sequence as its argument and returns a Boolean value indicating whether the element should be removed from the collection.

## Discussion

Use this method to remove every element in a collection that meets particular criteria. The order of the remaining elements is preserved. This example removes all the odd values from an array of numbers:

```
var numbers = [5, 6, 7, 8, 9, 10, 11]
numbers.removeAll(where: { $0 % 2 != 0 })
// numbers == [6, 8, 10]
```

Complexity

O(*n*), where *n* is the length of the collection.

