

- HealthKit
- HKQuantityTypeIdentifier
-  oxygenSaturation 

Type Property

# oxygenSaturation

A quantity sample type that measures the user’s oxygen saturation.

iOS 8.0+iPadOS 8.0+Mac Catalyst 13.0+macOS 13.0+visionOS 1.0+watchOS 2.0+

``` source
static let oxygenSaturation: HKQuantityTypeIdentifier
```

## Discussion

Oxygen saturation samples measure the percentage of oxygen in the bloodstream. These samples use percent units (described in HKUnit) and measure discrete values (described in HKQuantityAggregationStyle).

## See Also

### Vital signs

static let heartRate: HKQuantityTypeIdentifier

A quantity sample type that measures the user’s heart rate.

static let lowHeartRateEvent: HKCategoryTypeIdentifier

A category sample type for low heart rate events.

static let highHeartRateEvent: HKCategoryTypeIdentifier

A category sample type for high heart rate events.

static let irregularHeartRhythmEvent: HKCategoryTypeIdentifier

A category sample type for irregular heart rhythm events.

static let restingHeartRate: HKQuantityTypeIdentifier

A quantity sample type that measures the user’s resting heart rate.

static let heartRateVariabilitySDNN: HKQuantityTypeIdentifier

A quantity sample type that measures the standard deviation of heartbeat intervals.

static let heartRateRecoveryOneMinute: HKQuantityTypeIdentifier

A quantity sample that records the reduction in heart rate from the peak exercise rate to the rate one minute after exercising ended.

static let atrialFibrillationBurden: HKQuantityTypeIdentifier

A quantity type that measures an estimate of the percentage of time a person’s heart shows signs of atrial fibrillation (AFib) while wearing Apple Watch.

static let walkingHeartRateAverage: HKQuantityTypeIdentifier

A quantity sample type that measures the user’s heart rate while walking.

let HKDataTypeIdentifierHeartbeatSeries: String

A series sample containing heartbeat data.

class HKElectrocardiogramType

A type that identifies samples containing electrocardiogram data.

static let bodyTemperature: HKQuantityTypeIdentifier

A quantity sample type that measures the user’s body temperature.

static let bloodPressure: HKCorrelationTypeIdentifier

A correlation sample that combines a systolic sample and a diastolic sample into a single blood pressure reading.

static let bloodPressureSystolic: HKQuantityTypeIdentifier

A quantity sample type that measures the user’s systolic blood pressure.

static let bloodPressureDiastolic: HKQuantityTypeIdentifier

A quantity sample type that measures the user’s diastolic blood pressure.

