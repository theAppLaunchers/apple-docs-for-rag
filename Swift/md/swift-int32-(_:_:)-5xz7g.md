

- Swift
- Int32
-  \>\>(\_:\_:) 

Operator

# \>\>(\_:\_:)

Returns the result of shifting a value’s binary representation the specified number of digits to the right.

iOS 8.0+iPadOS 8.0+Mac Catalyst 13.0+macOS 10.10+tvOS 9.0+visionOS 1.0+watchOS 2.0+

``` source
static func >> (lhs: Self, rhs: Other) -> Self where Other : BinaryInteger
```

## Parameters 

`lhs`  

The value to shift.

`rhs`  

The number of bits to shift `lhs` to the right.

## Discussion

The `>>` operator performs a *smart shift*, which defines a result for a shift of any value.

- Using a negative value for `rhs` performs a left shift using `abs(rhs)`.

- Using a value for `rhs` that is greater than or equal to the bit width of `lhs` is an *overshift*. An overshift results in `-1` for a negative value of `lhs` or `0` for a nonnegative value.

- Using any other value for `rhs` performs a right shift on `lhs` by that amount.

The following example defines `x` as an instance of `UInt8`, an 8-bit, unsigned integer type. If you use `2` as the right-hand-side value in an operation on `x`, the value is shifted right by two bits.

```
let x: UInt8 = 30                 // 0b00011110
let y = x >> 2
// y == 7                         // 0b00000111
```

If you use `11` as `rhs`, `x` is overshifted such that all of its bits are set to zero.

```
let z = x >> 11
// z == 0                         // 0b00000000
```

Using a negative value as `rhs` is the same as performing a left shift using `abs(rhs)`.

```
let a = x >> -3
// a == 240                       // 0b11110000
let b = x 

Right shift operations on negative values “fill in” the high bits with ones instead of zeros.

```
let q: Int8 = -30                 // 0b11100010
let r = q >> 2
// r == -8                        // 0b11111000

let s = q >> 11
// s == -1                        // 0b11111111
```

