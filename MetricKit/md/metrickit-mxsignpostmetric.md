

- MetricKit
-  MXSignpostMetric 

Class

# MXSignpostMetric

An object representing a custom metric.

iOS 13.0+iPadOS 13.0+Mac Catalyst 13.1+visionOS 1.0+

``` source
class MXSignpostMetric
```

## Overview

A custom metric is an event type with a developer-defined name and category. You can add custom metrics to daily reports to capture information specific to your app.

Custom metrics are a type of signpost saved to custom OS logs created using makeLogHandle(category:). The daily report contains information about the number and duration of custom events, as well as the power and performance impact of those events. Only custom metric events logged using MetricKit utility functions capture additional power and performance data.

Note

The system limits the number of custom signpost metrics saved to the log in order to reduce on-device memory overhead. Limit use of custom metrics to critical sections of code.

## Topics

### Logging custom metrics

func mxSignpost(OSSignpostType, dso: UnsafeRawPointer, log: OSLog, name: StaticString, signpostID: OSSignpostID, StaticString, [any CVarArg])

Posts a single custom metric, the start time of a custom metric, or the end time of a custom metric to the log system.

func mxSignpostAnimationIntervalBegin(dso: UnsafeRawPointer, log: OSLog, name: StaticString, signpostID: OSSignpostID, StaticString, [any CVarArg])

Posts the start time of an animation interval to the log system.

### Reading custom metric data

var signpostIntervalData: MXSignpostIntervalData?

The data captured for a custom metric.

class MXSignpostIntervalData

A data object representing the captured data for a custom metric.

### Reading data about the custom metric

var signpostName: String

The developer-specified name of the custom metric represented by the object.

var signpostCategory: String

The developer-specified category of the custom metric represented by the object.

var totalCount: Int

The total number of occurrences of the captured custom metric.

## Relationships

### Inherits From

- MXMetric

### Conforms To

- CVarArg
- CustomDebugStringConvertible
- CustomStringConvertible
- Equatable
- Hashable
- NSCoding
- NSObjectProtocol
- NSSecureCoding

## See Also

### Related Documentation

Logging

Capture telemetry from your app for debugging and performance analysis using the unified logging system.

