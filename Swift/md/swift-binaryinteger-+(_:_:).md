

- Swift
- BinaryInteger
-  +(\_:\_:) 

Operator

# +(\_:\_:)

Adds two values and produces their sum.

iOS 8.0+iPadOS 8.0+Mac Catalyst 13.0+macOS 10.10+tvOS 9.0+visionOS 1.0+watchOS 2.0+

``` source
override static func + (lhs: Self, rhs: Self) -> Self
```

**Required**

## Parameters 

`lhs`  

The first value to add.

`rhs`  

The second value to add.

## Discussion

The addition operator (`+`) calculates the sum of its two arguments. For example:

```
1 + 2                   // 3
-10 + 15                // 5
-15 + -5                // -20
21.5 + 3.25             // 24.75
```

You cannot use `+` with arguments of different types. To add values of different types, convert one of the values to the other value’s type.

```
let x: Int8 = 21
let y: Int = 1000000
Int(x) + y              // 1000021
```

The sum of the two arguments must be representable in the arguments’ type. In the following example, the result of `21 + 120` is greater than the maximum representable `Int8` value:

```
x + 120                 // Overflow error
```

Note

Overflow checking is not performed in `-Ounchecked` builds.

If you want to opt out of overflow checking and wrap the result in case of any overflow, use the overflow addition operator (`&+`).

```
x &+ 120                // -115
```

## See Also

### Arithmetic

static func - (Self, Self) -> Self

Subtracts one value from another and produces their difference.

**Required**

static func * (Self, Self) -> Self

Multiplies two values and produces their product.

**Required**

static func / (Self, Self) -> Self

Returns the quotient of dividing the first value by the second.

**Required**

