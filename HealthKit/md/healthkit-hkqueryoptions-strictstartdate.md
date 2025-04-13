

- HealthKit
- HKQueryOptions
-  strictStartDate 

Type Property

# strictStartDate

The sample’s start time must fall within the target time period.

iOS 8.0+iPadOS 8.0+Mac Catalyst 13.0+macOS 13.0+visionOS 1.0+watchOS 2.0+

``` source
static var strictStartDate: HKQueryOptions { get }
```

## Discussion

The sample’s start time must be equal to or later than the target’s start time, and the sample’s start time must also be earlier than the target’s end time.

## See Also

### Constants

static var strictEndDate: HKQueryOptions

The sample’s end time must fall within the target time period.

