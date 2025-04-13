

- HealthKit
- HKQuantityTypeIdentifier
-  bloodGlucose 

Type Property

# bloodGlucose

A quantity sample type that measures the user’s blood glucose level.

iOS 8.0+iPadOS 8.0+Mac Catalyst 13.0+macOS 13.0+visionOS 1.0+watchOS 2.0+

``` source
static let bloodGlucose: HKQuantityTypeIdentifier
```

## Discussion

These samples use mass/volume units (described in HKUnit) and measure discrete values (described in HKQuantityAggregationStyle).

Please pay attention to the following issues while creating blood glucose samples:

- Blood glucose samples may be measured in mg/dL (milligrams per deciliter) or mmol/L (millimoles per liter), depending on the region.

- The Health app lets users select their preferred units. The Health app uses these units for both the display and manual entry of blood glucose samples.

- You can access the preferred units using the preferredUnits(for:completion:) method. If your app connects to a glucose meter that uses units other than the preferred units, alert the user. You can also recommend that users change their preferred units to match the glucose meter.

- Don’t save samples to HealthKit when the blood glucose meter is processing control solution.

## Topics

### Metadata Keys

let HKMetadataKeyBloodGlucoseMealTime: String

A key that indicates the relative timing of a blood glucose reading to a meal.

## See Also

### Related Documentation

struct HKQuantityTypeIdentifier

The identifiers that create quantity type objects.

class HKQuantitySample

A sample that represents a quantity, including the value and the units.

class HKQuantity

An object that stores a value for a given unit.

### Lab and test results

static let bloodAlcoholContent: HKQuantityTypeIdentifier

A quantity sample type that measures the user’s blood alcohol content.

static let electrodermalActivity: HKQuantityTypeIdentifier

A quantity sample type that measures electrodermal activity.

static let forcedExpiratoryVolume1: HKQuantityTypeIdentifier

A quantity sample type that measures the amount of air that can be forcibly exhaled from the lungs during the first second of a forced exhalation.

static let forcedVitalCapacity: HKQuantityTypeIdentifier

A quantity sample type that measures the amount of air that can be forcibly exhaled from the lungs after taking the deepest breath possible.

static let inhalerUsage: HKQuantityTypeIdentifier

A quantity sample type that measures the number of puffs the user takes from their inhaler.

static let insulinDelivery: HKQuantityTypeIdentifier

A quantity sample that measures the amount of insulin delivered.

static let numberOfTimesFallen: HKQuantityTypeIdentifier

A quantity sample type that measures the number of times the user fell.

static let peakExpiratoryFlowRate: HKQuantityTypeIdentifier

A quantity sample type that measures the user’s maximum flow rate generated during a forceful exhalation.

static let peripheralPerfusionIndex: HKQuantityTypeIdentifier

A quantity sample type that measures the user’s peripheral perfusion index.

