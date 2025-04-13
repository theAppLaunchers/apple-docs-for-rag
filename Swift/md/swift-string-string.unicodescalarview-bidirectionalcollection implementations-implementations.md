

- Swift
- String
- String.UnicodeScalarView
-  BidirectionalCollection Implementations 

API Collection

# BidirectionalCollection Implementations

## Topics

### Instance Properties

var endIndex: String.UnicodeScalarView.Index

The “past the end” position—that is, the position one greater than the last valid subscript argument.

var last: Self.Element?

The last element of the collection.

var startIndex: String.UnicodeScalarView.Index

The position of the first Unicode scalar value if the string is nonempty.

### Instance Methods

func difference&lt;C>(from: C) -> CollectionDifference&lt;Self.Element>

Returns the difference needed to produce this collection’s ordered elements from the given collection.

func difference&lt;C>(from: C, by: (C.Element, Self.Element) -> Bool) -> CollectionDifference&lt;Self.Element>

Returns the difference needed to produce this collection’s ordered elements from the given collection, using the given predicate as an equivalence test.

func distance(from: String.UnicodeScalarView.Index, to: String.UnicodeScalarView.Index) -> Int

Returns the distance between two indices.

func dropLast(Int) -> Self.SubSequence

Returns a subsequence containing all but the specified number of final elements.

func formIndex(before: inout Self.Index)

Replaces the given index with its predecessor.

func index(String.UnicodeScalarView.Index, offsetBy: Int) -> String.UnicodeScalarView.Index

Returns an index that is the specified distance from the given index.

func index(String.UnicodeScalarView.Index, offsetBy: Int, limitedBy: String.UnicodeScalarView.Index) -> String.UnicodeScalarView.Index?

Returns an index that is the specified distance from the given index, unless that distance is beyond a given limiting index.

func index(after: String.UnicodeScalarView.Index) -> String.UnicodeScalarView.Index

Returns the next consecutive location after `i`.

func index(before: String.UnicodeScalarView.Index) -> String.UnicodeScalarView.Index

Returns the previous consecutive location before `i`.

func last(where: (Self.Element) throws -> Bool) rethrows -> Self.Element?

Returns the last element of the sequence that satisfies the given predicate.

func lastIndex(of: Self.Element) -> Self.Index?

Returns the last index where the specified value appears in the collection.

func lastIndex(where: (Self.Element) throws -> Bool) rethrows -> Self.Index?

Returns the index of the last element in the collection that matches the given predicate.

func reversed() -> ReversedCollection&lt;Self>

Returns a view presenting the elements of the collection in reverse order.

func suffix(Int) -> Self.SubSequence

Returns a subsequence, up to the given maximum length, containing the final elements of the collection.

### Subscripts

subscript(String.UnicodeScalarView.Index) -> Unicode.Scalar

Accesses the Unicode scalar value at the given position.

subscript(Range&lt;String.UnicodeScalarView.Index>) -> String.UnicodeScalarView.SubSequence

Accesses a contiguous subrange of the collection’s elements.

