

- SwiftData
- HistoryTombstone
-  HistoryTombstone.Iterator 

Structure

# HistoryTombstone.Iterator

A type that provides the sequence’s iteration interface and encapsulates its iteration state.

iOS 18.0+iPadOS 18.0+Mac Catalyst 18.0+macOS 15.0+tvOS 18.0+visionOS 2.0+watchOS 11.0+Swift 5.9+

``` source
struct Iterator
```

## Topics

### Instance Methods

func next() -> Any?

Advances to the next element and returns it, or `nil` if no next element exists.

### Type Aliases

typealias Element

The type of element traversed by the iterator.

## Relationships

### Conforms To

- IteratorProtocol

