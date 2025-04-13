

- XCTest
- XCTOSSignpostMetric
-  scrollingAndDecelerationMetric 

Type Property

# scrollingAndDecelerationMetric

A metric that records scroll-dragging and deceleration animations.

iOS 15.0+iPadOS 15.0+Mac Catalyst 15.0+macOS 11.0+tvOS 15.0+visionOS 1.0+watchOS 8.0+

``` source
class var scrollingAndDecelerationMetric: any XCTMetric { get }
```

## Discussion

In a compatible iPad or iPhone app running in visionOS, the system doesn’t report hitch- or animation-related metrics that occur during scrolling.

