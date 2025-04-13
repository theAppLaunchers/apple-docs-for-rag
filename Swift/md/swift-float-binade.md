

- Swift
- Float
-  binade 

Instance Property

# binade

The floating-point value with the same sign and exponent as this value, but with a significand of 1.0.

iOS 8.0+iPadOS 8.0+Mac Catalyst 13.0+macOS 10.10+tvOS 9.0+visionOS 1.0+watchOS 2.0+

``` source
var binade: Float { get }
```

## Discussion

A *binade* is a set of binary floating-point values that all have the same sign and exponent. The `binade` property is a member of the same binade as this value, but with a unit significand.

In this example, `x` has a value of `21.5`, which is stored as `1.34375 * 2**4`, where `**` is exponentiation. Therefore, `x.binade` is equal to `1.0 * 2**4`, or `16.0`.

```
let x = 21.5
// x.significand == 1.34375
// x.exponent == 4

let y = x.binade
// y == 16.0
// y.significand == 1.0
// y.exponent == 4
```

## See Also

### Querying a Float

var ulp: Float

The unit in the last place of this value.

var significand: Float

The significand of the floating-point value.

var exponent: Int

The exponent of the floating-point value.

var nextUp: Float

The least representable value that compares greater than this value.

var nextDown: Self

The greatest representable value that compares less than this value.

