

- Combine
- AsyncPublisher
-  makeAsyncIterator() 

Instance Method

# makeAsyncIterator()

Creates the asynchronous iterator that produces elements of this asynchronous sequence.

iOS 15.0+iPadOS 15.0+Mac Catalyst 15.0+macOS 12.0+tvOS 15.0+visionOS 1.0+watchOS 8.0+

``` source
func makeAsyncIterator() -> AsyncPublisher.Iterator
```

## Return Value

An instance of the `AsyncIterator` type used to produce elements of the asynchronous sequence.

## See Also

### Creating an Iterator

struct Iterator

The iterator that produces elements of the asynchronous publisher sequence.

