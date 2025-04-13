

- Core Haptics
- CHHapticPatternPlayer
-  scheduleParameterCurve(\_:atTime:) 

Instance Method

# scheduleParameterCurve(\_:atTime:)

Schedules a parameter curve to begin transitioning a parameter at a certain time.

iOS 13.0+iPadOS 13.0+Mac Catalyst 13.0+macOS 10.15+tvOS 14.0+visionOS 1.0+

``` source
func scheduleParameterCurve(
    _ parameterCurve: CHHapticParameterCurve,
    atTime time: TimeInterval
) throws
```

**Required**

## Parameters 

`parameterCurve`  

The curve along which to vary the parameter.

`time`  

The time at which to begin applying the parameter curve.

## Discussion

Scheduling a parameter curve tells the haptic pattern player to vary a parameter gradually along the curve. For example, if the intensity of a haptic pattern is `0` at the time of application, then a curve created to set the haptic intensity to `1` will smoothly hit every single continuous value between `0` and `1` during the transition.

Scheduling a parameter curve is analogous to sending a dynamic parameter with sendParameters(_:atTime:); the only difference is that the curve transitions the parameter gradually, whereas the dynamic parameter changes the parameter immediately at a certain time.

- Swift
- Objective-C

```
let controlPoint = CHHapticParameterCurveControlPoint(relativeTime: 0.1, value: intensity)
let parameterCurve = CHHapticParameterCurve(parameterID: .hapticIntensityControl, controlPoints: [controlPoint], relativeTime: 0)
do {
    try continuousPlayer.scheduleParameterCurve(parameterCurve, atTime: 0)
} catch {
    print("Parameter Curve Error")
}
```

```
CHHapticParameterCurveControlPoint* intensityControlPoint = [[CHHapticParameterCurveControlPoint alloc] initWithRelativeTime:0.1 value:intensity];
CHHapticParameterCurve* intensityCurve = [[CHHapticParameterCurve alloc] initWithParameterID:CHHapticDynamicParameterIDHapticIntensityControl controlPoints:@[intensityControlPoint] relativeTime:0]; 
NSError* intensityCurveError;
[continuousPlayer scheduleParameterCurve:intensityCurve
                                  atTime:0
                                   error:&intensityCurveError];
```

Schedule a parameter curve for one parameter at a time, and specify control points to characterize the curve’s shape. For more information on creating or specifying a parameter curve, see CHHapticParameterCurve.

## See Also

### Sending Parameters to a Haptic

func sendParameters([CHHapticDynamicParameter], atTime: TimeInterval) throws

Sends an array of haptic parameters, starting at the specified time.

**Required**

