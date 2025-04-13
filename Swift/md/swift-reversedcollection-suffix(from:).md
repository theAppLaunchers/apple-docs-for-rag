

- Swift
- ReversedCollection
-  suffix(from:) 

Instance Method

# suffix(from:)

Returns a subsequence from the specified position to the end of the collection.

iOS 8.0+iPadOS 8.0+Mac Catalyst 13.0+macOS 10.10+tvOS 9.0+visionOS 1.0+watchOS 2.0+

``` source
func suffix(from start: Self.Index) -> Self.SubSequence
```

## Parameters 

`start`  

The index at which to start the resulting subsequence. `start` must be a valid index of the collection.

## Return Value

A subsequence starting at the `start` position.

## Discussion

The following example searches for the index of the number `40` in an array of integers, and then prints the suffix of the array starting at that index:

```
let numbers = [10, 20, 30, 40, 50, 60]
if let i = numbers.firstIndex(of: 40) {
    print(numbers.suffix(from: i))
}
// Prints "[40, 50, 60]"
```

Passing the collection’s `endIndex` as the `start` parameter results in an empty subsequence.

```
print(numbers.suffix(from: numbers.endIndex))
// Prints "[]"
```

Using the `suffix(from:)` method is equivalent to using a partial range from the index as the collection’s subscript. The subscript notation is preferred over `suffix(from:)`.

```
if let i = numbers.firstIndex(of: 40) {
    print(numbers[i...])
}
// Prints "[40, 50, 60]"
```

Complexity

O(1)

