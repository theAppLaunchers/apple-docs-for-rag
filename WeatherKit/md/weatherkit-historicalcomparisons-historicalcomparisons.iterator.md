

- WeatherKit
- HistoricalComparisons
-  HistoricalComparisons.Iterator 

Type Alias

# HistoricalComparisons.Iterator

A type that provides the collection’s iteration interface and encapsulates its iteration state.

iOS 18.0+iPadOS 18.0+Mac Catalyst 18.0+macOS 15.0+tvOS 18.0+visionOS 2.0+watchOS 11.0+

``` source
typealias Iterator = IndexingIterator
```

## Discussion

By default, a collection conforms to the `Sequence` protocol by supplying `IndexingIterator` as its associated `Iterator` type.

