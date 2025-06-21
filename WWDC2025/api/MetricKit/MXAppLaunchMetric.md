*   [MetricKit](/documentation/metrickit)
*   MXAppLaunchMetric

Class

# MXAppLaunchMetric

An object representing metrics about app launch time.

iOS 13.0+iPadOS 13.0+Mac Catalyst 13.1+macOS 10.15+visionOS 1.0+

```swift
```swift
```swift
```swift
```swift
```swift
```swift
```swift
class MXAppLaunchMetric
```
```
```
```
```
```
```
```

## [Topics](/documentation/MetricKit/MXAppLaunchMetric#topics)

### [Viewing app launch and resume time](/documentation/MetricKit/MXAppLaunchMetric#Viewing-app-launch-and-resume-time)

```swift
```swift
```swift
```swift
var histogrammedOptimizedTimeToFirstDraw: MXHistogram<UnitDuration>
```
```

A histogram of the different amounts of time associated with prewarmed app launches.
```
```swift
```swift
```swift
var histogrammedTimeToFirstDraw: MXHistogram<UnitDuration>
```
```

A histogram of the different amounts of time taken to launch the app.
```
```swift
```swift
```swift
var histogrammedApplicationResumeTime: MXHistogram<UnitDuration>
```
```

A histogram of the different amounts of time taken to resume the app from the background.
```
```swift
```swift
```swift
var histogrammedExtendedLaunch: MXHistogram<UnitDuration>
```
```

A histogram of the different amounts of time taken to launch the app, including the extended launch tasks.
```
```

## [Relationships](/documentation/MetricKit/MXAppLaunchMetric#relationships)

### [Inherits From](/documentation/MetricKit/MXAppLaunchMetric#inherits-from)

*   [`MXMetric`](/documentation/metrickit/mxmetric)

### [Conforms To](/documentation/MetricKit/MXAppLaunchMetric#conforms-to)

*   [`CVarArg`](/documentation/Swift/CVarArg)
*   [`CustomDebugStringConvertible`](/documentation/Swift/CustomDebugStringConvertible)
*   [`CustomStringConvertible`](/documentation/Swift/CustomStringConvertible)
*   [`Equatable`](/documentation/Swift/Equatable)
*   [`Hashable`](/documentation/Swift/Hashable)
*   [`NSCoding`](/documentation/Foundation/NSCoding)
*   [`NSObjectProtocol`](/documentation/ObjectiveC/NSObjectProtocol)
*   [`NSSecureCoding`](/documentation/Foundation/NSSecureCoding)

## [See Also](/documentation/MetricKit/MXAppLaunchMetric#see-also)

### [Responsiveness metrics](/documentation/MetricKit/MXAppLaunchMetric#Responsiveness-metrics)

```swift
```swift
```swift
```swift
class MXAnimationMetric
```
```

An object representing metrics about the responsiveness of animation in the app.
```
```swift
```swift
```swift
class MXAppResponsivenessMetric
```
```

An object representing metrics about the responsiveness of the app to user interaction.
```
```swift
```swift
```swift
class MXHangDiagnostic
```
```

An object representing a diagnostic report for an app that is too busy to handle user input responsively.
```
```