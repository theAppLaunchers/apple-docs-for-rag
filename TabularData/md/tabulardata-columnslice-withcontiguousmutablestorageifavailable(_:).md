

- TabularData
- ColumnSlice
-  withContiguousMutableStorageIfAvailable(\_:) 

Instance Method

# withContiguousMutableStorageIfAvailable(\_:)

Executes a closure on the collection’s contiguous storage.

TabularDataSwiftiOS 15.0+iPadOS 15.0+Mac Catalyst 15.0+macOS 12.0+tvOS 15.0+visionOS 1.0+watchOS 8.0+

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

### Allocating Contiguous Storage

func withContiguousStorageIfAvailable&lt;R>((UnsafeBufferPointer&lt;Self.Element>) throws -> R) rethrows -> R?

Executes a closure on the sequence’s contiguous storage.

