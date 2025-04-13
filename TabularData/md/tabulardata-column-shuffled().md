

- TabularData
- Column
-  shuffled() 

Instance Method

# shuffled()

Returns the elements of the sequence, shuffled.

TabularDataSwiftiOS 15.0+iPadOS 15.0+Mac Catalyst 15.0+macOS 12.0+tvOS 15.0+visionOS 1.0+watchOS 8.0+

``` source
func shuffled() -> [Self.Element]
```

## Return Value

A shuffled array of this sequence’s elements.

## Discussion

For example, you can shuffle the numbers between `0` and `9` by calling the `shuffled()` method on that range:

```
let numbers = 0...9
let shuffledNumbers = numbers.shuffled()
// shuffledNumbers == [1, 7, 6, 2, 8, 9, 4, 3, 5, 0]
```

This method is equivalent to calling `shuffled(using:)`, passing in the system’s default random generator.

Complexity

O(*n*), where *n* is the length of the sequence.

## See Also

### Generating Arrays

func sorted(by: (Self.Element, Self.Element) throws -> Bool) rethrows -> [Self.Element]

Returns the elements of the sequence, sorted using the given predicate as the comparison between elements.

func shuffled&lt;T>(using: inout T) -> [Self.Element]

Returns the elements of the sequence, shuffled using the given generator as a source for randomness.

func filter((Column&lt;WrappedElement>.Element) throws -> Bool) rethrows -> DiscontiguousColumnSlice&lt;WrappedElement>

Generates a slice that contains the elements that satisfy a predicate.

func compactMap&lt;ElementOfResult>((Self.Element) throws -> ElementOfResult?) rethrows -> [ElementOfResult]

Returns an array containing the non-`nil` results of calling the given transformation with each element of this sequence.

func flatMap&lt;SegmentOfResult>((Self.Element) throws -> SegmentOfResult) rethrows -> [SegmentOfResult.Element]

Returns an array containing the concatenated results of calling the given transformation with each element of this sequence.

func flatMap&lt;ElementOfResult>((Self.Element) throws -> ElementOfResult?) rethrows -> [ElementOfResult]

