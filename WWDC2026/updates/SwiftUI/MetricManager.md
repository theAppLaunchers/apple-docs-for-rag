- MetricKit
- MetricManager

Class

# MetricManager

An object that delivers metric and diagnostic reports to your app.

iOS 27.0+ iPadOS 27.0+ Mac Catalyst 27.0+ macOS 27.0+ visionOS 27.0+

```swift
final class MetricManager
```

## Mentioned in

Monitoring app performance with MetricKit

## Discussion

MetricManager is an instantiable class rather than a shared singleton. Create an instance and hold it for as long as you need reports. Share that instance across your app rather than creating multiple instances with the same domains. If you create more than one MetricManager, two tasks concurrently iterating the same sequence both receive a non-deterministic subset of reports rather than a full copy.

Metric reports arrive through metricReports, and diagnostic reports through diagnosticReports. Both are typed AsyncSequence properties that never throw, so you iterate them with for await in long-lived tasks:

```swift
let manager = MetricManager()


Task {
    for await report in manager.metricReports {
        process(report)
    }
}
Task {
    for await report in manager.diagnosticReports {
        process(report)
    }
}
```

To receive metrics segmented by app state, pass a set of StateReportingDomain values to init(enabledStateReportingDomains:). When state reporting is enabled, stateEntries carries metrics grouped by each recorded state in addition to the standard intervalEntries.

## Topics

Initialization

convenience init()

Creates a new MetricManager instance without state reporting domains.

init(enabledStateReportingDomains: Set<StateReportingDomain>)

Creates a new MetricManager instance with state reporting domains enabled for metrics aggregation.

var enabledStateReportingDomains: Set<StateReportingDomain>

StateReporting domains enabled for metrics aggregation

### Reports

var metricReports: some AsyncSequence<MetricReport, Never>

An asynchronous sequence that delivers daily metric reports.

var diagnosticReports: some AsyncSequence<DiagnosticReport, Never>

An asynchronous sequence that delivers diagnostic reports as individual events.

### Custom metric logs

static func logHandle(category: String) -> OSLog

Returns an OSLog handle for creating custom signpost metrics that MetricKit aggregates.

### Extended launch

func trackLaunchTask<Result, Failure>(id: LaunchTaskID, onTrackingError: ((MetricManager.LaunchTaskError) -> Void)?, () async throws(Failure) -> Result) async throws(Failure) -> Result

Measures the duration of an asynchronous extended launch task.

func trackLaunchTask<Result, Failure>(id: LaunchTaskID, onTrackingError: ((MetricManager.LaunchTaskError) -> Void)?, () throws(Failure) -> Result) throws(Failure) -> Result

Measures the duration of a synchronous extended launch task.

struct LaunchTaskError

An error that describes a problem that occurred while tracking an extended launch task.

struct LaunchTaskID

An identifier for a task measured as part of an extended app launch.

### State-contextualized metrics

struct ReportedState

A recorded app state associated with a metric or diagnostic report entry.

## Relationships

### Conforms To

- Sendable
- SendableMetatype

## See Also

### Metric and diagnostic reports

struct MetricReport

A daily performance report that contains metric values for your app.

struct DiagnosticReport

A report describing a single diagnostic event.