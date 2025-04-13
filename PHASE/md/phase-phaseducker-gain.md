

- PHASE
- PHASEDucker
-  gain 

Instance Property

# gain

The amount of volume reduction.

iOS 15.0+iPadOS 15.0+Mac Catalyst 15.0+macOS 12.0+tvOS 17.0+visionOS 1.0+

``` source
var gain: Double { get }
```

## Discussion

When source and target sounds play simultaneously, the value of this property determines the amount that the listener can hear the target sound. A value of `0` results in full attenuation, and `1` results in no attenuation. The framework clamps the value to the range between `0` and `1`.

## See Also

### Configuring Volume Reduction

var identifier: String

A unique value for the ducker.

var isActive: Bool

A Boolean value that determines whether the ducker reduces sound.

var attackTime: Double

The amount of time for sound reduction to reach maximum strength.

var attackCurve: PHASECurveType

A mathematical curve that shapes transition progress as sound reduction begins.

var releaseTime: Double

The amount of time to transition from maximum sound reduction to no reduction.

var releaseCurve: PHASECurveType

A mathematical curve that shapes transition progress as sound reduction ends.

