

- Swift
- Double
-  formRemainder(dividingBy:) 

Instance Method

# formRemainder(dividingBy:)

Replaces this value with the remainder of itself divided by the given value.

iOS 8.0+iPadOS 8.0+Mac Catalyst 13.0+macOS 10.10+tvOS 9.0+visionOS 1.0+watchOS 2.0+

``` source
mutating func formRemainder(dividingBy other: Double)
```

## Parameters 

`other`  

The value to use when dividing this value.

## Discussion

For two finite values `x` and `y`, the remainder `r` of dividing `x` by `y` satisfies `x == y * q + r`, where `q` is the integer nearest to `x / y`. If `x / y` is exactly halfway between two integers, `q` is chosen to be even. Note that `q` is *not* `x / y` computed in floating-point arithmetic, and that `q` may not be representable in any available integer type.

The following example calculates the remainder of dividing 8.625 by 0.75:

```
var x = 8.625
print(x / 0.75)
// Prints "11.5"

let q = (x / 0.75).rounded(.toNearestOrEven)
// q == 12.0
x.formRemainder(dividingBy: 0.75)
// x == -0.375

let x1 = 0.75 * q + x
// x1 == 8.625
```

If this value and `other` are finite numbers, the remainder is in the closed range `-abs(other / 2)...abs(other / 2)`. The `formRemainder(dividingBy:)` method is always exact.

## See Also

### Performing Calculations

Floating-Point Operators for Double

Perform arithmetic and bitwise operations or compare values.

func addingProduct(Self, Self) -> Self

Returns the result of adding the product of the two given values to this value, computed without intermediate rounding.

func addProduct(Double, Double)

Adds the product of the two given values to this value in place, computed without intermediate rounding.

func squareRoot() -> Self

Returns the square root of the value, rounded to a representable value.

func formSquareRoot()

Replaces this value with its square root, rounded to a representable value.

func remainder(dividingBy: Self) -> Self

Returns the remainder of this value divided by the given value.

func truncatingRemainder(dividingBy: Self) -> Self

Returns the remainder of this value divided by the given value using truncating division.

func formTruncatingRemainder(dividingBy: Double)

Replaces this value with the remainder of itself divided by the given value using truncating division.

func negate()

Replaces this value with its additive inverse.

