

- SensorKit
-  SRPhotoplethysmogramOpticalSample 

Class

# SRPhotoplethysmogramOpticalSample

A data sample from the photoplethysmogram (PPG) optical sensor.

iOS 17.4+iPadOS 17.4+Mac Catalyst 17.4+

``` source
class SRPhotoplethysmogramOpticalSample
```

## Overview

To get the PPG waveform, use the normalizedReflectance property. Apple Watch uses an arrangement of emitters and photodiodes to measure the PPG waveform.

### Interpret second-generation PPG sensors data

Second-generation optical heart sensors, in Apple Watch 4, 5, and SE models, use green or infrared (IR) LED lights paired with light-sensitive photodiodes. The active photodiode’s indices show which photodiode or combination of photodiodes the Apple Watch uses.

For the second-generation sensors, the mapping of the optical heart sensor (SE, Series 4 and 5) emitter is:

| Emitter index | LED arrangement      |
|---------------|----------------------|
| 0             | 0, Infrared (940 nm) |
| 1             | 1, Infrared (940 nm) |
| 2             | 2, Green (525 nm)    |
| 3             | 3, Green (525 nm)    |
| 4             | 4, Green (525 nm)    |
| 5             | 5, Green (525 nm)    |

### Interpret third-generation PPG sensors

Third-generation optical heart sensor, in Apple Watch Series 6 and later, plus Apple Watch Ultra and Ultra 2, use an additional red LED with a different arrangement of emitters and photodiodes than the second-generation PPG sensors. The active photodiodes indices show which photodiode or combination of photodiodes the Apple Watch uses.

For the third-generation sensors, the mapping of the optical heart sensor (Series 6, 7, 8, 9, Ultra, and Ultra 2) emitter is:

| Emitter index | LED arrangement      |
|---------------|----------------------|
| 0             | 0, Infrared (850 nm) |
| 1             | 1, Infrared (850 nm) |
| 2             | 2, Infrared (850 nm) |
| 3             | 3, Infrared (850 nm) |
| 4             | 4, Infrared (940 nm) |
| 5             | 5, Red (660 nm)      |
| 6             | 6, Red (660 nm)      |
| 7             | 7, Red (660 nm)      |
| 8             | 8, Red (660 nm)      |
| 9             | 9, Green (525 nm)    |
| 10            | 10, Green (525 nm)   |
| 11            | 11, Green (525 nm)   |
| 12            | 12, Green (525 nm)   |

## Topics

### Accessing optical data

var emitter: Int

The index of the LED in use during the sample.

var activePhotodiodeIndexes: IndexSet

The set of photodiodes in use during the sample.

var signalIdentifier: Int

The identifier for a signal that photodiodes and emitters produce.

var nominalWavelength: Measurement&lt;UnitLength>

The wavelength in nanometers that the emitter produces while operating at a specific temperature.

var effectiveWavelength: Measurement&lt;UnitLength>

A temperature-compensated wavelength estimate in nanometers that the emitter produces.

var samplingFrequency: Measurement&lt;UnitFrequency>

The sampling frequency of the photoplethysmogram (PPG) data in hertz.

var nanosecondsSinceStart: Int64

The time in nanoseconds since the system turns on the sensor.

var conditions: [SRPhotoplethysmogramOpticalSample.Condition]

The sensor context or conditions that may affect the sample.

struct Condition

The conditions that may occur when recording photoplethysmogram optical data.

var noiseTerms: SRPhotoplethysmogramOpticalSample.NoiseTerms?

The mathematical terms for computing the noise in this sample.

struct NoiseTerms

The mathematical terms that you use to compute the photoplethysmogram (PPG) noise.

var normalizedReflectance: Double?

The normalized photoplethysmogram (PPG) waveform.

## Relationships

### Inherits From

- NSObject

### Conforms To

- CVarArg
- CustomDebugStringConvertible
- CustomStringConvertible
- Equatable
- Hashable
- NSCoding
- NSCopying
- NSObjectProtocol
- NSSecureCoding
- Sendable

## See Also

### Accessing PPG data

var startDate: Date

The start date of the photoplethysmogram (PPG) sensor data recording.

var nanosecondsSinceStart: Int64

The time in nanoseconds since the start of the data recording.

var usage: [SRPhotoplethysmogramSample.Usage]

The method that the person or system uses to take the reading.

struct Usage

The possible ways that a person or the system may take a photoplethysmogram (PPG) reading.

var opticalSamples: [SRPhotoplethysmogramOpticalSample]

The samples recorded by the photoplethysmogram (PPG) optical sensor.

var accelerometerSamples: [SRPhotoplethysmogramAccelerometerSample]

The samples recorded by the photoplethysmogram (PPG) accelerometer.

class SRPhotoplethysmogramAccelerometerSample

A data sample from the photoplethysmogram (PPG) accelerometer.

var temperature: Measurement&lt;UnitTemperature>?

The samples recorded by the photoplethysmogram (PPG) thermometer.

