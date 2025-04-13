

- Swift
- AsyncDropFirstSequence
-  dropFirst(\_:) 

Instance Method

# dropFirst(\_:)

Omits a specified number of elements from the base asynchronous sequence, then passes through all remaining elements.

iOS 13.0+iPadOS 13.0+Mac Catalyst 13.0+macOS 10.15+tvOS 13.0+visionOS 1.0+watchOS 6.0+

``` source
func dropFirst(_ count: Int = 1) -> AsyncDropFirstSequence
```

Available when `Base` conforms to `AsyncSequence`.

## Discussion

When you call `dropFirst(_:)` on an asynchronous sequence that is already an `AsyncDropFirstSequence`, the returned sequence simply adds the new drop count to the current drop count.

