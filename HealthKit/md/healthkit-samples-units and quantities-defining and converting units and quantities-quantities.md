

- HealthKit
- Samples
- Units and quantities
-  Defining and converting units and quantities 

Article

# Defining and converting units and quantities

Create and convert units and quantities.

## Overview

The HKUnit class provides the representation for a single unit. It supports a wide range of metric and imperial units, as well as both simple and complex units. A simple unit represents a single measurement, such as meters, pounds, or seconds. A complex unit combines one or more simple units using mathematical operations, such as meters per second (m/s) or pounds per square foot (lb/ft2).

In addition to convenience methods for creating all the simple units supported by HealthKit, HKUnit provides the mathematical operations needed to build complex units. You can also create complex units directly using properly formatted unit strings.

For more information on units, see HKUnit.

The HKQuantity class stores a value for a given unit. You can then request the value in any compatible units, letting your app easily translate values between units.

For more information on quantities, see HKQuantity.

You can use MeasurementFormatter to localize quantities such as length, mass, and energy. For other quantities, you need to perform the conversions and localize the data yourself.

## See Also

### Units and quantities

class HKQuantity

An object that stores a value for a given unit.

class HKUnit

A class for managing the units of measure within HealthKit.

enum HKMetricPrefix

Prefixes that can be added to SI units to change the order of magnitude.

