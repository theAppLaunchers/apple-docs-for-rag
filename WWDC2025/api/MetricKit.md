Framework

# MetricKit

Aggregate and analyze per-device reports on exception and crash diagnostics and on power and performance metrics.

iOS 13.0+iPadOS 13.0+Mac Catalyst 13.0+macOS 12.0+visionOS 1.0+

## [Overview](/documentation/MetricKit#overview)

With MetricKit, you can receive on-device app diagnostics and power and performance metrics the system captures. The system delivers metric reports about the previous 24 hours to a registered app at most once per day, and delivers diagnostic reports immediately in iOS 15 and later and macOS 12 and later. This framework supports diagnostics for crashes, hangs, energy, and disk writes for apps running in visionOS but doesn’t report metrics for apps running in visionOS. This includes apps built for visionOS or compatible iPhone and iPad apps running in visionOS.

Use the data in the reports to help improve the performance of your iOS app, macOS app, or Mac app built with Mac Catalyst. The framework includes the following:

*   A manager class and a subscriber protocol
    
*   Payload classes for reported data
    
*   Classes for each category of metrics and diagnostics
    
*   Classes for measurement units, such as bars of cellular connectivity
    
*   Classes for representing accumulated data, such as histograms
    
*   A class for capturing stack traces in diagnostics
    

## [Topics](/documentation/MetricKit#topics)

### [Essentials](/documentation/MetricKit#Essentials)

```swift
```swift
```swift
```swift
class MXMetricManager
```
```

The shared object that registers you to receive metrics, creates logs for custom metrics, and gives access to past reports.
```
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

### [Performance improvements](/documentation/MetricKit#Performance-improvements)

[

Improving your app’s performance](/documentation/Xcode/improving-your-app-s-performance)

Model, measure, and boost the performance of your app by using a continuous-improvement cycle.

### [Battery metrics](/documentation/MetricKit#Battery-metrics)

```swift
```swift
```swift
```swift
class MXCellularConditionMetric
```
```

An object representing metrics about the condition of the cellular network.
```
```swift
```swift
```swift
class MXCPUMetric
```
```

An object representing metrics about the use of the CPU.
```
```swift
```swift
```swift
class MXDisplayMetric
```
```

An object representing metrics about the power used to display the app on the screen.
```
```swift
```swift
```swift
class MXGPUMetric
```
```

An object representing metrics about the use of the GPU.
```
```swift
```swift
```swift
class MXLocationActivityMetric
```
```

An object representing metrics about the use of location-tracking features of a device.
```
```swift
```swift
```swift
class MXNetworkTransferMetric
```
```

An object representing metrics about network transfers.
```
```swift
```swift
```swift
class MXCPUExceptionDiagnostic
```
```

An object representing a diagnostic report for a fatal or nonfatal CPU exception.
```
```

### [Performance metrics](/documentation/MetricKit#Performance-metrics)

```swift
```swift
```swift
```swift
class MXAppLaunchDiagnostic
```
```

A diagnostic subclass that encapsulates app launch diagnostic reports.
```
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

### [Responsiveness metrics](/documentation/MetricKit#Responsiveness-metrics)

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
class MXAppLaunchMetric
```
```

An object representing metrics about app launch time.
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

### [Disk usage metrics](/documentation/MetricKit#Disk-usage-metrics)

```swift
```swift
```swift
```swift
class MXDiskIOMetric
```
```

An object representing metrics about disk usage.
```
```swift
```swift
```swift
class MXDiskSpaceUsageMetric
```
```

An object representing metrics about your app’s disk space usage.

Beta
```
```swift
```swift
```swift
class MXDiskWriteExceptionDiagnostic
```
```

An object representing a diagnostic report for a disk write exception.
```
```

### [Custom metrics](/documentation/MetricKit#Custom-metrics)

```swift
```swift
```swift
```swift
class MXSignpostMetric
```
```

An object representing a custom metric.
```
```

### [Data types](/documentation/MetricKit#Data-types)

```swift
```swift
```swift
```swift
class MXCallStackTree
```
```

An object representing the call stack for an exception.
```
```swift
```swift
```swift
class MXMetaData
```
```

An object containing system-level information about the device.
```
```swift
```swift
```swift
class MXAverage
```
```

A unit of measure for an average.
```
```swift
```swift
```swift
class MXHistogram
```
```

An object representing a histogram of data values of the same type of unit.
```
```swift
```swift
```swift
class MXDiagnostic
```
```

An abstract data class for a diagnostic.
```
```swift
```swift
```swift
class MXMetric
```
```

An abstract data class for a metric.
```
```swift
```swift
```swift
enum Code
```
```

Error codes for error values from app metrics.
```
```swift
```swift
```swift
let MXErrorDomain: String
```
```

Error domain for error values from app metrics.
```
```swift
```swift
```swift
struct MXError
```
```

Error domain for error handling of app metrics.
```
```swift
```swift
```swift
class MXCrashDiagnosticObjectiveCExceptionReason
```
```

An object that represents the exception reason for an uncaught ObjC exception.
```
```swift
```swift
```swift
class MXSignpostRecord
```
```

An object representing the record for a signpost interval or event.
```
```