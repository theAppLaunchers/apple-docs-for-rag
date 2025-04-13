

- Xcode
- Performance and metrics
- Reducing your app’s memory use
-  Responding to low-memory warnings 

Article

# Responding to low-memory warnings

Detect when your app is using excessive memory, and bring memory use under control.

## Overview

iOS sends your app a warning when its memory use approaches the limit of available device memory. The amount of memory use that triggers a memory warning corresponds to the yellow region in Xcode’s memory gauge. Your app can receive a memory warning in any of these ways:

- UIKit calls the applicationDidReceiveMemoryWarning(_:) method of your app delegate.

- UIKit calls the didReceiveMemoryWarning() method of active UIViewController objects.

- iOS posts didReceiveMemoryWarningNotification to the default notification center.

- Dispatch queues receive an event with source type DISPATCH_SOURCE_TYPE_MEMORYPRESSURE.

The operating system sends low-memory warnings using a best-effort approach, and your app needs to respond to them as quickly as possible. If memory demand on the system increases faster than the warnings relieve memory pressure, the system may not have time to send the low-memory warnings and wait for apps to respond. When this occurs, the system resorts to jettisoning apps to reclaim their memory and recording the reason in a log file, as described in Identifying high-memory use with jetsam event reports.

Make sure your app changes its approach for allocating memory when it receives a memory warning—adopting a conservative policy of looking for opportunities to release objects or reduce their size as it uses them. If your app allocates large amounts of memory at once and crashes before it receives the low-memory warning during the large allocation, modify your code to slowly allocate the necessary memory, so the system has adequate time to free memory from across the system.

If your app loads data it can easily recreate, consider using NSPurgeableData. When the contents of NSPurgeableData aren’t marked as in-use through beginContentAccess(), the system automatically discards the contents in low-memory situations. This automatic discard process helps your app react to a low-memory warnings more quickly, because the kernel handles discarding the data, rather than your app, which is waiting to receive the low-memory notification before discarding the data.

Important

Don’t traverse your app’s whole object graph looking for memory to release when your app receives a memory warning, and avoid using NSCache in connection with NSPurgeableData. iOS compresses memory pages that apps haven’t accessed recently. Searching for memory to purge brings these pages out of the compressor, and increases memory demands on the system.

## See Also

### Related Documentation

Identifying high-memory use with jetsam event reports

Discover why the operating system terminated your app when available memory was low.

### Tasks

Gathering information about memory use

Identify memory-use inefficiencies by measuring and profiling your app.

Making changes to reduce memory use

Decrease your app’s use of memory by addressing common causes of excessive use.

Preventing memory-use regressions

Measure the memory that your app’s features use, and detect increases by using XCTest performance tests.

