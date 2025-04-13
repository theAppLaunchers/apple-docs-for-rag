

- Swift
- Float16
-  init(exactly:) 

Initializer

# init(exactly:)

Creates a new instance initialized to the given value, if it can be represented without rounding.

iOS 14.0+iPadOS 14.0+Mac Catalyst 14.0+macOS 11.0+tvOS 14.0+visionOS 1.0+watchOS 7.0+

``` source
init?(exactly other: Double)
```

## Parameters 

`other`  

The value to use for the new instance.

## Discussion

If `other` can’t be represented as an instance of `Float16` without rounding, the result of this initializer is `nil`. In particular, passing NaN as `other` always results in `nil`.

```
let x: Double = 21.25
let y = Float16(exactly: x)
// y == Optional.some(21.25)

let z = Float16(exactly: Double.nan)
// z == nil
```

