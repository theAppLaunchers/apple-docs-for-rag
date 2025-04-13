

- Xcode
- Performance and metrics
- Reducing your app’s memory use
-  Preventing memory-use regressions 

Article

# Preventing memory-use regressions

Measure the memory that your app’s features use, and detect increases by using XCTest performance tests.

## Overview

XCTest can measure the amount of memory allocated by your app while it executes a test case. To measure memory use, create a performance test in your app’s unit test target, and pass an instance of XCTMemoryMetric to `measure(metrics:)`. Inside the block, call the code from your app that demonstrates the problematic memory use.

```
class MemoryTests: XCTestCase {
    func testMemoryUse() {
        self.measure(metrics: [XCTMemoryMetric()]) {
          // Use the relevant app feature here
        }
    }
}
```

When you run this test, Xcode measures the peak memory use observed while the block runs, and the growth in memory allocated between the block’s beginning and end. You can observe these values by clicking the icon next to the test results. Click Set Baseline to establish a value for future comparisons. The test fails if the memory use significantly exceeds the baseline measurement.

## See Also

### Tasks

Gathering information about memory use

Identify memory-use inefficiencies by measuring and profiling your app.

Making changes to reduce memory use

Decrease your app’s use of memory by addressing common causes of excessive use.

Responding to low-memory warnings

Detect when your app is using excessive memory, and bring memory use under control.

