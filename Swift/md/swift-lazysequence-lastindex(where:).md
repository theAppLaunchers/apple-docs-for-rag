

- Swift
- LazySequence
-  lastIndex(where:) 

Instance Method

# lastIndex(where:)

Returns the index of the last element in the collection that matches the given predicate.

iOS 8.0+iPadOS 8.0+Mac Catalyst 13.0+macOS 10.10+tvOS 9.0+visionOS 1.0+watchOS 2.0+

``` source
func lastIndex(where predicate: (Self.Element) throws -> Bool) rethrows -> Self.Index?
```

## Parameters 

`predicate`  

A closure that takes an element as its argument and returns a Boolean value that indicates whether the passed element represents a match.

## Return Value

The index of the last element in the collection that matches `predicate`, or `nil` if no elements match.

## Discussion

You can use the predicate to find an element of a type that doesn’t conform to the `Equatable` protocol or to find an element that matches particular criteria. This example finds the index of the last name that begins with the letter *A:*

```
let students = ["Kofi", "Abena", "Peter", "Kweku", "Akosua"]
if let i = students.lastIndex(where: { $0.hasPrefix("A") }) {
    print("\(students[i]) starts with 'A'!")
}
// Prints "Akosua starts with 'A'!"
```

Complexity

O(*n*), where *n* is the length of the collection.

