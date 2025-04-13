

- Swift
- Float16
-  leastNormalMagnitude 

Type Property

# leastNormalMagnitude

The least positive normal number.

iOS 14.0+iPadOS 14.0+Mac Catalyst 14.0+macOS 11.0+tvOS 14.0+visionOS 1.0+watchOS 7.0+

``` source
static var leastNormalMagnitude: Float16 { get }
```

## Discussion

This value compares less than or equal to all positive normal numbers. There may be smaller positive numbers, but they are *subnormal*, meaning that they are represented with less precision than normal numbers.

This value corresponds to type-specific C macros such as `FLT_MIN` and `DBL_MIN`. The naming of those macros is slightly misleading, because subnormals, zeros, and negative numbers are smaller than this value.

