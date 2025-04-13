

- Swift
- ReversedCollection
-  ReversedCollection.Element 

Type Alias

# ReversedCollection.Element

A type that represents a valid position in the collection.

iOS 8.0+iPadOS 8.0+Mac Catalyst 13.0+macOS 10.10+tvOS 9.0+visionOS 1.0+watchOS 2.0+

``` source
typealias Element = Base.Element
```

Available when `Base` conforms to `BidirectionalCollection`.

## Discussion

Valid indices consist of the position of every element and a “past the end” position that’s not valid for use as a subscript.

