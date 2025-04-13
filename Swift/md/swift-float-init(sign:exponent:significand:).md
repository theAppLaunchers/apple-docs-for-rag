

- Swift
- Float
-  init(sign:exponent:significand:) 

Initializer

# init(sign:exponent:significand:)

Creates a new value from the given sign, exponent, and significand.

iOS 8.0+iPadOS 8.0+Mac Catalyst 13.0+macOS 10.10+tvOS 9.0+visionOS 1.0+watchOS 2.0+

``` source
init(
    sign: FloatingPointSign,
    exponent: Int,
    significand: Float
)
```

## Parameters 

`sign`  

The sign to use for the new value.

`exponent`  

The new value’s exponent.

`significand`  

The new value’s significand.

## Discussion

The following example uses this initializer to create a new `Double` instance. `Double` is a binary floating-point type that has a radix of `2`.

```
let x = Double(sign: .plus, exponent: -2, significand: 1.5)
// x == 0.375
```

This initializer is equivalent to the following calculation, where `**` is exponentiation, computed as if by a single, correctly rounded, floating-point operation:

```
let sign: FloatingPointSign = .plus
let exponent = -2
let significand = 1.5
let y = (sign == .minus ? -1 : 1) * significand * Double.radix ** exponent
// y == 0.375
```

As with any basic operation, if this value is outside the representable range of the type, overflow or underflow occurs, and zero, a subnormal value, or infinity may result. In addition, there are two other edge cases:

- If the value you pass to `significand` is zero or infinite, the result is zero or infinite, regardless of the value of `exponent`.

- If the value you pass to `significand` is NaN, the result is NaN.

For any floating-point value `x` of type `F`, the result of the following is equal to `x`, with the distinction that the result is canonicalized if `x` is in a noncanonical encoding:

```
let x0 = F(sign: x.sign, exponent: x.exponent, significand: x.significand)
```

This initializer implements the `scaleB` operation defined by the IEEE 754 specification.

## See Also

### Converting Floating-Point Values

init&lt;Source>(Source)

Creates a new instance from the given value, rounded to the closest possible representation.

init&lt;Source>(Source)

Creates a new value, rounded to the closest possible representation.

init(Double)

Creates a new instance that approximates the given value.

init(Float)

Creates a new instance initialized to the given value.

init(Float80)

Creates a new instance that approximates the given value.

init(CGFloat)

init(Float16)

Creates a new instance that approximates the given value.

init(signOf: Float, magnitudeOf: Float)

Creates a new floating-point value using the sign of one value and the magnitude of another.

init(truncating: NSNumber)

