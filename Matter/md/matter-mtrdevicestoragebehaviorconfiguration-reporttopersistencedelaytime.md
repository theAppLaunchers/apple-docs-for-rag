

- Matter
- MTRDeviceStorageBehaviorConfiguration
-  reportToPersistenceDelayTime 

Instance Property

# reportToPersistenceDelayTime

If any of these properties are set to be out of the documented limits, these default values will be used to replace all of them:

iOS 17.6+iPadOS 17.6+Mac Catalyst 17.6+macOS 14.6+tvOS 17.6+visionOS 1.0+watchOS 10.6+

``` source
var reportToPersistenceDelayTime: TimeInterval { get set }
```

## Discussion

reportToPersistenceDelayTimeDefault (15) reportToPersistenceDelayTimeMaxDefault (20 \* 15) recentReportTimesMaxCountDefault (12) timeBetweenReportsTooShortThresholdDefault (15) timeBetweenReportsTooShortMinThresholdDefault (5) reportToPersistenceDelayMaxMultiplierDefault (10) deviceReportingExcessivelyIntervalThresholdDefault (5 \* 60)

