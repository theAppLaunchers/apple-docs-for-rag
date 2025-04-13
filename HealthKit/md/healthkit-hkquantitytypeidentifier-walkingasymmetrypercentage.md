

- HealthKit
- HKQuantityTypeIdentifier
-  walkingAsymmetryPercentage 

Type Property

# walkingAsymmetryPercentage

A quantity sample type that measures the percentage of steps in which one foot moves at a different speed than the other when walking on flat ground.

iOS 14.0+iPadOS 14.0+Mac Catalyst 14.0+macOS 13.0+visionOS 1.0+watchOS 7.0+

``` source
static let walkingAsymmetryPercentage: HKQuantityTypeIdentifier
```

## Discussion

Walking asymmetry is the percent of time that a user’s steps with one foot are faster or slower than the other foot. The system automatically records walking asymmetry samples on iPhone 8 or later. The user must carry their phone near their waist—such as in a pocket—and walk steadily on flat ground. The system records the phone’s location using the HKMetadataKeyDevicePlacementSide metadata key. The system records 10 to 30 walking asymmetry samples on a typical day. iPhone doesn’t record walking asymmetry samples if the user’s wheelchair status is on.

These samples use percentage units (described in HKUnit) and measure discrete values (described in HKQuantityAggregationStyle). For example, the following code creates a percentage unit.

```
let percentage = HKUnit.percent()
```

The sample’s quantity property represents the percent of asymmetrical steps between the sample’s startDate and endDate properties.

## See Also

### Related Documentation

enum HKDevicePlacementSide

Values that indicate the placement of the device that measured a sample.

### Mobility

static let appleWalkingSteadiness: HKQuantityTypeIdentifier

A quantity sample type that measures the steadiness of the user’s gait.

static let appleWalkingSteadinessEvent: HKCategoryTypeIdentifier

A category sample type that records an incident where the user showed a reduced score for their gait’s steadiness.

static let sixMinuteWalkTestDistance: HKQuantityTypeIdentifier

A quantity sample type that stores the distance a user can walk during a six-minute walk test.

static let walkingSpeed: HKQuantityTypeIdentifier

A quantity sample type that measures the user’s average speed when walking steadily over flat ground.

static let walkingStepLength: HKQuantityTypeIdentifier

A quantity sample type that measures the average length of the user’s step when walking steadily over flat ground.

static let walkingDoubleSupportPercentage: HKQuantityTypeIdentifier

A quantity sample type that measures the percentage of time when both of the user’s feet touch the ground while walking steadily over flat ground.

static let stairAscentSpeed: HKQuantityTypeIdentifier

A quantity sample type measuring the user’s speed while climbing a flight of stairs.

static let stairDescentSpeed: HKQuantityTypeIdentifier

A quantity sample type measuring the user’s speed while descending a flight of stairs.

