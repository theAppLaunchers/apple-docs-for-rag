

- HealthKit
- HKQuantityTypeIdentifier
-  walkingSpeed 

Type Property

# walkingSpeed

A quantity sample type that measures the user’s average speed when walking steadily over flat ground.

iOS 14.0+iPadOS 14.0+Mac Catalyst 14.0+macOS 13.0+visionOS 1.0+watchOS 7.0+

``` source
static let walkingSpeed: HKQuantityTypeIdentifier
```

## Discussion

Walking speed represents how quickly the user walks on flat ground. The system automatically records walking speed samples on iPhone 8 or later. The user must carry their phone near their waist—such as in a pocket—and walk steadily on flat ground. To ensure accuracy, the user’s height value must be up to date. The system records 10 to 30 walking speed samples on a typical day. iPhone doesn’t record walking speed samples if the user’s wheelchair status is on.

These samples use distance per time units (described in HKUnit) and measure discrete values (described in HKQuantityAggregationStyle). For example, the following code shows two ways to create a meters per second unit. The first uses explicit constructors, while the second initializes the unit from a string.

```
let mps = HKUnit.meter().unitDivided(by: HKUnit.second())
let mpsFromString = HKUnit(from: "m/s")
```

The sample’s quantity property represents the average walking speed between the sample’s startDate and endDate properties.

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

static let walkingStepLength: HKQuantityTypeIdentifier

A quantity sample type that measures the average length of the user’s step when walking steadily over flat ground.

static let walkingAsymmetryPercentage: HKQuantityTypeIdentifier

A quantity sample type that measures the percentage of steps in which one foot moves at a different speed than the other when walking on flat ground.

static let walkingDoubleSupportPercentage: HKQuantityTypeIdentifier

A quantity sample type that measures the percentage of time when both of the user’s feet touch the ground while walking steadily over flat ground.

static let stairAscentSpeed: HKQuantityTypeIdentifier

A quantity sample type measuring the user’s speed while climbing a flight of stairs.

static let stairDescentSpeed: HKQuantityTypeIdentifier

A quantity sample type measuring the user’s speed while descending a flight of stairs.

