

- Xcode
- Performance and metrics
-  Reducing your app’s memory use 

# Reducing your app’s memory use

Improve your app’s performance by analyzing memory-use metrics and making changes to maximize memory efficiency.

## Overview

The memory (RAM) on a device is a limited resource that’s shared by apps, operating system processes, and the kernel. iOS has techniques for satisfying the various demands on memory, but these techniques come at the expense of speed and responsiveness. For example, iOS might transfer a memory-intensive app to solid-state storage when the app is running in the background. The app then incurs a delay when coming back to the foreground or attempting to run a background task.

If the app is using too much memory, iOS sends it a warning. You get notifications of such warnings in the form of a *crash report*. This report, with an `EXC_RESOURCE` exception type and `MEMORY` subtype, indicates that the app has approached its memory limit. It doesn’t mean that iOS has terminated the app, only that it has detected a memory-use problem. The memory limit that triggers the exception depends on the device, and once an app exceeds this limit, iOS terminates it. If the app is terminated when it’s in the foreground, the user sees it disappear. The next time the user opens the app, it launches from the beginning, which takes longer than resuming from the background.

Because the device shares memory between apps and iOS processes, one app using too much memory can compromise the user experience across the whole device. Limiting the amount of memory an app uses can benefit users even when they’re using other apps.

### Understand memory-use metrics

The Xcode Organizer and MetricKit each provide two metrics about memory use in an app. The first metric is peak memory use, which is the highest memory use observed in any of the samples taken. iOS collects this metric by sampling the app’s memory use periodically throughout the day. The second metric is memory use observed on suspension, measured when the app enters the background.

iOS measures memory use as the number of memory pages in use multiplied by page size, which is typically 16 KB. Writing a single byte to allocated memory can increase memory use by 16 KB if iOS must allocate a new page to store that byte.

Data structures defined in the app’s executable or linked libraries and frameworks contribute to the memory-use metric. Memory that the app allocates at runtime doesn’t initially contribute to this metric. Such memory is “clean,” and iOS doesn’t need to dedicate physical RAM to store it. When the app writes to the allocated memory, it becomes “dirty,” and iOS dedicates RAM to storing its content, as shown in the illustration below. Dirty memory contributes to the memory-use metric.

### View data on memory use

View your app’s memory use in the Memory pane of the Xcode Organizer window or by using MetricKit.

The Memory pane shows information for peak memory in the top graph and memory at suspension on the bottom. Filter the information by device type and by typical memory used (50th percentile) or top memory used (90th percentile), using the two menus in the top right corner, to find possible problem areas. Compare the memory use of the current release with a previous one by clicking on bar in the graph for the desired release.

## Topics

### Tasks

Gathering information about memory use

Identify memory-use inefficiencies by measuring and profiling your app.

Making changes to reduce memory use

Decrease your app’s use of memory by addressing common causes of excessive use.

Preventing memory-use regressions

Measure the memory that your app’s features use, and detect increases by using XCTest performance tests.

Responding to low-memory warnings

Detect when your app is using excessive memory, and bring memory use under control.

## See Also

### Related Documentation

Identifying high-memory use with jetsam event reports

Discover why the operating system terminated your app when available memory was low.

### Memory and size

Reducing your app’s size

Measure your app’s size, optimize its assets and settings, and adopt technologies that help streamline installation over a mobile internet connection.

