

- Swift
- Float80
-  init(exactly:) 

Initializer

# init(exactly:)

Creates a new instance initialized to the given value, if it can be represented without rounding.

macOS 10.10+

``` source
init?(exactly other: Float80)
```

## Parameters 

`other`  

The value to use for the new instance.

## Discussion

If `other` can’t be represented as an instance of `Float80` without rounding, the result of this initializer is `nil`. In particular, passing NaN as `other` always results in `nil`.

```
let x: Float80 = 21.25
let y = Float80(exactly: x)
// y == Optional.some(21.25)

let z = Float80(exactly: Float80.nan)
// z == nil
```

