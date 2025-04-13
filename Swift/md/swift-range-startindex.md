

- Swift
- Range
-  startIndex 

Instance Property

# startIndex

The position of the first element in a nonempty collection.

iOS 8.0+iPadOS 8.0+Mac Catalyst 13.0+macOS 10.10+tvOS 9.0+visionOS 1.0+watchOS 2.0+

``` source
var startIndex: Range.Index { get }
```

Available when `Bound` conforms to `Strideable` and `Bound.Stride` conforms to `SignedInteger`.

## Discussion

If the collection is empty, `startIndex` is equal to `endIndex`.

