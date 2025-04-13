

- RealityKit
- JointTransforms
-  withContiguousMutableStorageIfAvailable(\_:) 

Instance Method

# withContiguousMutableStorageIfAvailable(\_:)

Executes a closure on the collection’s contiguous storage.

RealityKitSwiftiOSiPadOSMac CatalystmacOSvisionOS

``` source
mutating func withContiguousMutableStorageIfAvailable(_ body: (inout UnsafeMutableBufferPointer) throws -> R) rethrows -> R?
```

## Parameters 

`body`  

A closure that receives an in-out `UnsafeMutableBufferPointer` to the collection’s contiguous storage.

## Return Value

The value returned from `body`, unless the collection doesn’t support contiguous storage, in which case the method ignores `body` and returns `nil`.

## Discussion

This method calls `body(buffer)`, where `buffer` provides access to the contiguous mutable storage of the entire collection. If the contiguous storage doesn’t exist, the collection creates it. If the collection doesn’t support an internal representation in the form of contiguous mutable storage, this method doesn’t call `body` — it immediately returns `nil`.

The optimizer can often eliminate bounds- and uniqueness-checking within an algorithm. When that fails, however, invoking the same algorithm on the `buffer` argument may let you trade safety for speed.

Always perform any necessary cleanup in the closure, because the method makes no guarantees about the state of the collection if the closure throws an error. Your changes to the collection may be absent from the collection after throwing the error, because the closure could receive a temporary copy rather than direct access to the collection’s storage.

Warning

Your `body` closure must not replace `buffer`. This leads to a crash in all implementations of this method within the standard library.

Successive calls to this method may provide a different pointer on each call. Don’t store `buffer` outside of this method.

A `Collection` that provides its own implementation of this method must provide contiguous storage to its elements in the same order as they appear in the collection. This guarantees that it’s possible to generate contiguous mutable storage to any of its subsequences by slicing `buffer` with a range formed from the distances to the subsequence’s `startIndex` and `endIndex`, respectively.

## See Also

### Accessing joint transforms

subscript(JointTransforms.Index) -> Transform

Accesses a single joint transform in the collection at the given index.

func allSatisfy((Self.Element) throws -> Bool) rethrows -> Bool

Returns a Boolean value indicating whether every element of a sequence satisfies a given predicate.

func compactMap&lt;ElementOfResult>((Self.Element) throws -> ElementOfResult?) rethrows -> [ElementOfResult]

Returns an array containing the non-`nil` results of calling the given transformation with each element of this sequence.

func contains(Self.Element) -> Bool

Returns a Boolean value indicating whether the sequence contains the given element.

func contains(where: (Self.Element) throws -> Bool) rethrows -> Bool

Returns a Boolean value indicating whether the sequence contains an element that satisfies the given predicate.

func difference&lt;C>(from: C) -> CollectionDifference&lt;Self.Element>

Returns the difference needed to produce this collection’s ordered elements from the given collection.

func difference&lt;C>(from: C, by: (C.Element, Self.Element) -> Bool) -> CollectionDifference&lt;Self.Element>

Returns the difference needed to produce this collection’s ordered elements from the given collection, using the given predicate as an equivalence test.

func distance(from: Self.Index, to: Self.Index) -> Int

func drop(while: (Self.Element) throws -> Bool) rethrows -> Self.SubSequence

Returns a subsequence by skipping elements while `predicate` returns `true` and returning the remaining elements.

func dropFirst(Int) -> Self.SubSequence

Returns a subsequence containing all but the given number of initial elements.

func dropLast(Int) -> Self.SubSequence

Returns a subsequence containing all but the specified number of final elements.

func elementsEqual&lt;OtherSequence>(OtherSequence) -> Bool

Returns a Boolean value indicating whether this sequence and another sequence contain the same elements in the same order.

func elementsEqual&lt;OtherSequence>(OtherSequence, by: (Self.Element, OtherSequence.Element) throws -> Bool) rethrows -> Bool

Returns a Boolean value indicating whether this sequence and another sequence contain equivalent elements in the same order, using the given predicate as the equivalence test.

func enumerated() -> EnumeratedSequence&lt;Self>

Returns a sequence of pairs (*n*, *x*), where *n* represents a consecutive integer starting at zero and *x* represents an element of the sequence.

func filter((Self.Element) throws -> Bool) rethrows -> [Self.Element]

Returns an array containing, in order, the elements of the sequence that satisfy the given predicate.

