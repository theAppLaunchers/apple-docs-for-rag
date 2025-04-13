

- Create ML Components
- VideoReader
- VideoReader.CameraAsyncBuffers
-  dropFirst(\_:) 

Instance Method

# dropFirst(\_:)

Omits a specified number of elements from the base asynchronous sequence, then passes through all remaining elements.

Create ML ComponentsSwiftiOS 13.0+iPadOS 13.0+Mac Catalyst 13.0+macOS 10.15+tvOS 13.0+visionOS 1.0+watchOS 6.0+

``` source
func dropFirst(_ count: Int = 1) -> AsyncDropFirstSequence
```

## Parameters 

`count`  

The number of elements to drop from the beginning of the sequence. `count` must be greater than or equal to zero.

## Return Value

An asynchronous sequence that drops the first `count` elements from the base sequence.

## Discussion

Use `dropFirst(_:)` when you want to drop the first *n* elements from the base sequence and pass through the remaining elements.

In this example, an asynchronous sequence called `Counter` produces `Int` values from `1` to `10`. The `dropFirst(_:)` method causes the modified sequence to ignore the values `1` through `3`, and instead emit `4` through `10`:

```
for await number in Counter(howHigh: 10).dropFirst(3) {
    print(number, terminator: " ")
}
// Prints "4 5 6 7 8 9 10 "
```

If the number of elements to drop exceeds the number of elements in the sequence, the result is an empty sequence.

