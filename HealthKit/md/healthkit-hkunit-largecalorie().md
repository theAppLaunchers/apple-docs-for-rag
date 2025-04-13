

- HealthKit
- HKUnit
-  largeCalorie() 

Type Method

# largeCalorie()

Returns a HealthKit unit for measuring energy in large calories (Cal).

iOS 11.0+iPadOS 11.0+Mac Catalyst 13.0+macOS 13.0+visionOS 1.0+watchOS 4.0+

``` source
class func largeCalorie() -> Self
```

## Discussion

The large calorie is the same as a kilocalorie (1 Cal = 4184.0 J).

## See Also

### Constructing energy units

class func joule() -> Self

Returns a HealthKit unit for measuring energy in joules.

class func jouleUnit(with: HKMetricPrefix) -> Self

Returns a HealthKit unit for measuring energy, using joule units with the provided prefix.

class func kilocalorie() -> Self

Returns a HealthKit unit for measuring energy in kilocalories.

class func smallCalorie() -> Self

Returns a HealthKit unit for measuring energy in small calories (cal).

class func calorie() -> Self

Returns a HealthKit unit for measuring energy in calories.

Deprecated

