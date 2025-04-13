

- Swift
- Int32
-  &\*=(\_:\_:) 

Operator

# &\*=(\_:\_:)

Multiplies two values and stores the result in the left-hand-side variable, wrapping any overflow.

iOS 8.0+iPadOS 8.0+Mac Catalyst 13.0+macOS 10.10+tvOS 9.0+visionOS 1.0+watchOS 2.0+

``` source
static func &*= (lhs: inout Self, rhs: Self)
```

## Parameters 

`lhs`  

The first value to multiply.

`rhs`  

The second value to multiply.

## Discussion

The masking multiplication assignment operator (`&*=`) silently wraps any overflow that occurs during the operation. In the following example, the product of `10` and `50` is greater than the maximum representable `Int8` value, so the result is the partial value after discarding the overflowing bits.

```
var x: Int8 = 10
x &*= 5
// x == 50
var y: Int8 = 10
y &*= 50
// y == -12 (after overflow)
```

For more about arithmetic with overflow operators, see Overflow Operators in *The Swift Programming Language*.

