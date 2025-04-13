

- Create ML
- MLDataTable
- MLDataTable.Rows
-  prefix(through:) 

Instance Method

# prefix(through:)

Returns a subsequence from the start of the collection through the specified position.

Create MLSwiftiOS 15.0+iPadOS 15.0+Mac Catalyst 15.0+macOS 10.14+tvOS 16.0+visionOS 1.0+

``` source
func prefix(through position: Self.Index) -> Self.SubSequence
```

## Parameters 

`position`  

The index of the last element to include in the resulting subsequence. `position` must be a valid index of the collection that is not equal to the `endIndex` property.

## Return Value

A subsequence up to, and including, the given position.

## Discussion

The resulting subsequence *includes* the element at the position specified by the `through` parameter. The following example searches for the index of the number `40` in an array of integers, and then prints the prefix of the array up to, and including, that index:

```
let numbers = [10, 20, 30, 40, 50, 60]
if let i = numbers.firstIndex(of: 40) {
    print(numbers.prefix(through: i))
}
// Prints "[10, 20, 30, 40]"
```

Using the `prefix(through:)` method is equivalent to using a partial closed range as the collection’s subscript. The subscript notation is preferred over `prefix(through:)`.

```
if let i = numbers.firstIndex(of: 40) {
    print(numbers[...i])
}
// Prints "[10, 20, 30, 40]"
```

Complexity

O(1)

## See Also

### Selecting rows

func prefix(Int) -> Self.SubSequence

Returns a subsequence, up to the specified maximum length, containing the initial elements of the collection.

func prefix(upTo: Self.Index) -> Self.SubSequence

Returns a subsequence from the start of the collection up to, but not including, the specified position.

func prefix(while: (Self.Element) throws -> Bool) rethrows -> Self.SubSequence

Returns a subsequence containing the initial elements until `predicate` returns `false` and skipping the remaining elements.

func suffix(Int) -> Self.SubSequence

Returns a subsequence, up to the given maximum length, containing the final elements of the collection.

func suffix(from: Self.Index) -> Self.SubSequence

Returns a subsequence from the specified position to the end of the collection.

