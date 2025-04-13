

- Swift
- FloatingPoint
-  isZero 

Instance Property

# isZero

A Boolean value indicating whether the instance is equal to zero.

iOS 8.0+iPadOS 8.0+Mac Catalyst 13.0+macOS 10.10+tvOS 9.0+visionOS 1.0+watchOS 2.0+

``` source
var isZero: Bool { get }
```

**Required**

## Discussion

The `isZero` property of a value `x` is `true` when `x` represents either `-0.0` or `+0.0`. `x.isZero` is equivalent to the following comparison: `x == 0.0`.

```
let x = -0.0
x.isZero        // true
x == 0.0        // true
```

