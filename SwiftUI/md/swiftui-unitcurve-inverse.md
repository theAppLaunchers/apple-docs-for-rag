

- SwiftUI
- UnitCurve
-  inverse 

Instance Property

# inverse

Returns a copy of the curve with its x and y components swapped.

iOS 17.0+iPadOS 17.0+Mac Catalyst 17.0+macOS 14.0+tvOS 17.0+visionOS 1.0+watchOS 10.0+

``` source
var inverse: UnitCurve { get }
```

## Discussion

The inverse can be used to solve a curve in reverse: given a known output (y) value, the corresponding input (x) value can be found by using `inverse`:

```
let curve = UnitCurve.easeInOut

/// The input time for which an easeInOut curve returns 0.6.
let inputTime = curve.inverse.evaluate(at: 0.6)
```

