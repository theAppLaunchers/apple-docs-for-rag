

- Swift
- Double
-  isNaN 

Instance Property

# isNaN

A Boolean value indicating whether the instance is NaN (“not a number”).

iOS 8.0+iPadOS 8.0+Mac Catalyst 13.0+macOS 10.10+tvOS 9.0+visionOS 1.0+watchOS 2.0+

``` source
var isNaN: Bool { get }
```

## Discussion

Because NaN is not equal to any value, including NaN, use this property instead of the equal-to operator (`==`) or not-equal-to operator (`!=`) to test whether a value is or is not NaN. For example:

```
let x = 0.0
let y = x * .infinity
// y is a NaN

// Comparing with the equal-to operator never returns 'true'
print(x == Double.nan)
// Prints "false"
print(y == Double.nan)
// Prints "false"

// Test with the 'isNaN' property instead
print(x.isNaN)
// Prints "false"
print(y.isNaN)
// Prints "true"
```

This property is `true` for both quiet and signaling NaNs.

## See Also

### Querying a Double’s State

var isZero: Bool

A Boolean value indicating whether the instance is equal to zero.

var isFinite: Bool

A Boolean value indicating whether this instance is finite.

var isInfinite: Bool

A Boolean value indicating whether the instance is infinite.

var isSignalingNaN: Bool

A Boolean value indicating whether the instance is a signaling NaN.

var isNormal: Bool

A Boolean value indicating whether this instance is normal.

var isSubnormal: Bool

A Boolean value indicating whether the instance is subnormal.

var isCanonical: Bool

A Boolean value indicating whether the instance’s representation is in its canonical form.

var floatingPointClass: FloatingPointClassification

The classification of this value.

