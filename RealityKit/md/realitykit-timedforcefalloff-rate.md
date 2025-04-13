

- RealityKit
- TimedForceFalloff
-  rate 

Instance Property

# rate

The temporal falloff / attenuation rate.

iOS 18.0+iPadOS 18.0+Mac Catalyst 18.0+macOS 15.0+visionOS 2.0+

``` source
var rate: Double
```

## Discussion

An exponent that determines how the effect’s strength diminishes over time. Use a non-negative rate.

- When the rate is **0**, no falloff occurs.

- When the rate is **greater than 0 and less than 1.0**, falloff occurs slower and is sublinear.

- When the rate is **1.0**, falloff is linear.

- When the rate is **greater than 1**, falloff occurs faster and is nonlinear.

