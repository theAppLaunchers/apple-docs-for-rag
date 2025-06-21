*   [MetricKit](/documentation/metrickit)
*   MXMetricManager

Class

# MXMetricManager

The shared object that registers you to receive metrics, creates logs for custom metrics, and gives access to past reports.

iOS 13.0+iPadOS 13.0+Mac Catalyst 13.1+macOS 12.0+visionOS 1.0+

```swift
```swift
```swift
```swift
```swift
```swift
```swift
```swift
class MXMetricManager
```
```
```
```
```
```
```
```

## [Overview](/documentation/MetricKit/MXMetricManager#overview)

The `MXMetricManager` shared object manages your subscription for receiving on-device daily metrics.

MetricKit starts accumulating reports for your app after calling [`shared`](/documentation/metrickit/mxmetricmanager/shared) for the first time. To receive the reports, call [`add(_:)`](/documentation/metrickit/mxmetricmanager/add\(_:\)) with an object that adopts the [`MXMetricManagerSubscriber`](/documentation/metrickit/mxmetricmanagersubscriber) protocol. The system then delivers metric reports at most once per day, and diagnostic reports immediately in iOS 15 and later and macOS 12 and later. The reports contain the metrics from the past 24 hours and any previously undelivered daily reports. To pause receiving reports, call [`remove(_:)`](/documentation/metrickit/mxmetricmanager/remove\(_:\)).

The calls to add a subscriber and for receiving reports are safe to use in performance-sensitive code, such as app launch.

The snippet below shows a simple class for using MetricKit.

```swift
```swift
```swift
```swift
```swift
```swift
class AppMetrics: NSObject, MXMetricManagerSubscriber {
```
```
    func receiveReports() {
       let shared = MXMetricManager.shared
       shared.add(self)
    }
    func pauseReports() {
       let shared = MXMetricManager.shared
       shared.remove(self)
    }
    // Receive daily metrics.
    func didReceive(_ payloads: [MXMetricPayload]) {
       // Process metrics.
    }
    // Receive diagnostics immediately when available.
    func didReceive(_ payloads: [MXDiagnosticPayload]) {
       // Process diagnostics.
    }
}
```
```
```
```

Note

MetricKit delivers daily metric reports from iOS 13 or later, and macOS 26 or later.

## [Topics](/documentation/MetricKit/MXMetricManager#topics)

### [Getting the shared metrics manager](/documentation/MetricKit/MXMetricManager#Getting-the-shared-metrics-manager)

```swift
```swift
```swift
```swift
class var shared: MXMetricManager
```
```

An object that returns the shared metrics manager instance.
```
```

### [Subscribing to reports](/documentation/MetricKit/MXMetricManager#Subscribing-to-reports)

```swift
```swift
```swift
```swift
func add(any MXMetricManagerSubscriber)
```
```

Registers to receive a daily report of app metrics from the metrics manager.
```
```swift
```swift
```swift
func remove(any MXMetricManagerSubscriber)
```
```

Unsubscribes from daily reports of app metrics.
```
```

### [Retrieving previous reports](/documentation/MetricKit/MXMetricManager#Retrieving-previous-reports)

```swift
```swift
```swift
```swift
var pastPayloads: [MXMetricPayload]
```
```

Returns an array of the daily metrics reports generated since the last allocation of the shared manager instance.
```
```swift
```swift
```swift
var pastDiagnosticPayloads: [MXDiagnosticPayload]
```
```

Returns an array of the diagnostic reports generated since the last allocation of the shared manager instance.
```
```

### [Creating custom metric logs](/documentation/MetricKit/MXMetricManager#Creating-custom-metric-logs)

```swift
```swift
```swift
```swift
class func makeLogHandle(category: String) -> OSLog
```
```

Returns a log handle used for writing custom metric events.
```
```

### [Measuring an extended launch](/documentation/MetricKit/MXMetricManager#Measuring-an-extended-launch)

```swift
```swift
```swift
```swift
class func extendLaunchMeasurement(forTaskID: MXLaunchTaskID) throws
```
```

Starts to measure an extended launch task with the given task identifier.
```
```swift
```swift
```swift
class func finishExtendedLaunchMeasurement(forTaskID: MXLaunchTaskID) throws
```
```

Signals the end of an extended launch task.
```
```swift
```swift
```swift
struct MXLaunchTaskID
```
```

The task identifier to track launch measurements.
```
```

## [Relationships](/documentation/MetricKit/MXMetricManager#relationships)

### [Inherits From](/documentation/MetricKit/MXMetricManager#inherits-from)

*   [`NSObject`](/documentation/ObjectiveC/NSObject-swift.class)

### [Conforms To](/documentation/MetricKit/MXMetricManager#conforms-to)

*   [`CVarArg`](/documentation/Swift/CVarArg)
*   [`CustomDebugStringConvertible`](/documentation/Swift/CustomDebugStringConvertible)
*   [`CustomStringConvertible`](/documentation/Swift/CustomStringConvertible)
*   [`Equatable`](/documentation/Swift/Equatable)
*   [`Hashable`](/documentation/Swift/Hashable)
*   [`NSObjectProtocol`](/documentation/ObjectiveC/NSObjectProtocol)

## [See Also](/documentation/MetricKit/MXMetricManager#see-also)

### [Essentials](/documentation/MetricKit/MXMetricManager#Essentials)

```swift
```swift
```swift
```swift
class MXMetricPayload
```
```

An object that encapsulates a daily metrics report.
```
```swift
```swift
```swift
class MXDiagnosticPayload
```
```

An object that encapsulates a diagnostic report.
```
```swift
```swift
```swift
protocol MXMetricManagerSubscriber
```
```

A protocol defining a method for receiving a daily metrics report.
```
```