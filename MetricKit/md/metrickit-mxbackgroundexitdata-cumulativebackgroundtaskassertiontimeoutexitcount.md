

- MetricKit
- MXBackgroundExitData
-  cumulativeBackgroundTaskAssertionTimeoutExitCount 

Instance Property

# cumulativeBackgroundTaskAssertionTimeoutExitCount

The number of times the system terminated the app from the background for exceeding the allocated time for a background task.

iOS 14.0+iPadOS 14.0+Mac Catalyst 14.0+visionOS 1.0+

``` source
var cumulativeBackgroundTaskAssertionTimeoutExitCount: Int { get }
```

## Discussion

This exit usually occurs when the app fails to call endBackgroundTask(_:) as soon as a background task is complete.

