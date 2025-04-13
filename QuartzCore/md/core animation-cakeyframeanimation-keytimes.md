

- Core Animation
- CAKeyframeAnimation
-  keyTimes 

Instance Property

# keyTimes

An optional array of `NSNumber` objects that define the time at which to apply a given keyframe segment.

iOS 2.0+iPadOS 2.0+Mac Catalyst 13.1+macOS 10.5+tvOS 9.0+visionOS 1.0+

``` source
var keyTimes: [NSNumber]? { get set }
```

## Discussion

Each value in the array is a floating point number between `0.0` and `1.0` that defines the time point (specified as a fraction of the animation’s total duration) at which to apply the corresponding keyframe value. Each successive value in the array must be greater than, or equal to, the previous value. Usually, the number of elements in the array should match the number of elements in the values property or the number of control points in the path property. If they do not, the timing of your animation might not be what you expect.

The appropriate values to include in the array are dependent on the calculationMode property.

- If the calculationMode is set to linear or cubic, the first value in the array must be `0.0` and the last value must be `1.0`. All intermediate values represent time points between the start and end times.

- If the calculationMode is set to discrete, the first value in the array must be `0.0` and the last value must be `1.0`. The array should have one more entry than appears in the values array. For example, if there are two values, there should be three key times.

- If the calculationMode is set to paced or cubicPaced, the values in this property are ignored.

If the values in this array are invalid or inappropriate for the current calculation mode, they are ignored.

## See Also

### Keyframe timing

var timingFunctions: [CAMediaTimingFunction]?

An optional array of `CAMediaTimingFunction` objects that define the pacing for each keyframe segment.

var calculationMode: CAAnimationCalculationMode

Specifies how intermediate keyframe values are calculated by the receiver.

