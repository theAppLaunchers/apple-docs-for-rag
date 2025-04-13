

- Swift
- Float16
-  +(\_:\_:) 

Operator

# +(\_:\_:)

Adds two values and produces their sum, rounded to a representable value.

iOS 14.0+iPadOS 14.0+Mac Catalyst 14.0+macOS 11.0+tvOS 14.0+visionOS 1.0+watchOS 7.0+

``` source
static func + (lhs: Float16, rhs: Float16) -> Float16
```

## Parameters 

`lhs`  

The first value to add.

`rhs`  

The second value to add.

## Discussion

The addition operator (`+`) calculates the sum of its two arguments. For example:

```
let x = 1.5
let y = x + 2.25
// y == 3.75
```

The `+` operator implements the addition operation defined by the IEEE 754 specification.

