

- Swift
- ClosedRange
-  clamped(to:) 

Instance Method

# clamped(to:)

Returns a copy of this range clamped to the given limiting range.

iOS 8.0+iPadOS 8.0+Mac Catalyst 13.0+macOS 10.10+tvOS 9.0+visionOS 1.0+watchOS 2.0+

``` source
func clamped(to limits: ClosedRange) -> ClosedRange
```

Available when `Bound` conforms to `Comparable`.

## Parameters 

`limits`  

The range to clamp the bounds of this range.

## Return Value

A new range clamped to the bounds of `limits`.

## Discussion

The bounds of the result are always limited to the bounds of `limits`. For example:

```
let x: ClosedRange = 0...20
print(x.clamped(to: 10...1000))
// Prints "10...20"
```

If the two ranges do not overlap, the result is a single-element range at the upper or lower bound of `limits`.

```
let y: ClosedRange = 0...5
print(y.clamped(to: 10...1000))
// Prints "10...10"
```

