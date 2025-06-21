*   [MetricKit](/documentation/metrickit)
*   MXAppLaunchDiagnostic

Class

# MXAppLaunchDiagnostic

A diagnostic subclass that encapsulates app launch diagnostic reports.

iOS 16.0+iPadOS 16.0+Mac Catalyst 16.0+visionOS 1.0+

```swift
```swift
```swift
```swift
```swift
```swift
```swift
```swift
class MXAppLaunchDiagnostic
```
```
```
```
```
```
```
```

## [Topics](/documentation/MetricKit/MXAppLaunchDiagnostic#topics)

### [Reading app launch metrics](/documentation/MetricKit/MXAppLaunchDiagnostic#Reading-app-launch-metrics)

```swift
```swift
```swift
```swift
var callStackTree: MXCallStackTree
```
```

The call stack tree associated with the app launch.
```
```swift
```swift
```swift
var launchDuration: Measurement<UnitDuration>
```
```

The total app launch duration.
```
```

## [Relationships](/documentation/MetricKit/MXAppLaunchDiagnostic#relationships)

### [Inherits From](/documentation/MetricKit/MXAppLaunchDiagnostic#inherits-from)

*   [`MXDiagnostic`](/documentation/metrickit/mxdiagnostic)

### [Conforms To](/documentation/MetricKit/MXAppLaunchDiagnostic#conforms-to)

*   [`CVarArg`](/documentation/Swift/CVarArg)
*   [`CustomDebugStringConvertible`](/documentation/Swift/CustomDebugStringConvertible)
*   [`CustomStringConvertible`](/documentation/Swift/CustomStringConvertible)
*   [`Equatable`](/documentation/Swift/Equatable)
*   [`Hashable`](/documentation/Swift/Hashable)
*   [`NSCoding`](/documentation/Foundation/NSCoding)
*   [`NSObjectProtocol`](/documentation/ObjectiveC/NSObjectProtocol)
*   [`NSSecureCoding`](/documentation/Foundation/NSSecureCoding)

## [See Also](/documentation/MetricKit/MXAppLaunchDiagnostic#see-also)

### [Performance metrics](/documentation/MetricKit/MXAppLaunchDiagnostic#Performance-metrics)

```swift
```swift
```swift
```swift
class MXAppExitMetric
```
```

An object representing metrics about the types of foreground and background app exits.
```
```swift
```swift
```swift
class MXAppRunTimeMetric
```
```

An object representing metrics about the amount of time the app is active.
```
```swift
```swift
```swift
class MXMemoryMetric
```
```

An object representing metrics about the app’s memory use.
```
```swift
```swift
```swift
class MXCrashDiagnostic
```
```

An object representing a diagnostic report for an app crash.
```
```