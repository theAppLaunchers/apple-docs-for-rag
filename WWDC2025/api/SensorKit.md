Framework

# SensorKit

Retrieve data and derived metrics from sensors on an iPhone, or paired Apple Watch.

iOS 14.0+iPadOS 14.0+

## [Overview](/documentation/SensorKit#overview)

As the system gathers information using various sensors on a device, SensorKit enables an app to access select raw data, or metrics that the system processes from a sensor, such as:

*   Steps information
    
*   Accelerometer or rotation-rate data
    
*   The configuration of a watch on the user’s wrist
    
*   Ambient light in the physical environment
    
*   Details about a user’s routine commute or travel
    

See [`SRSensor`](/documentation/sensorkit/srsensor) for the complete list.

Note

This framework ignores calls from Mac apps that you build with Mac Catalyst, and from compatible iPad and iPhone apps running in visionOS.

## [Topics](/documentation/SensorKit#topics)

### [Essentials](/documentation/SensorKit#Essentials)

[

SensorKit updates](/documentation/Updates/SensorKit)

Learn about important changes to SensorKit.

### [Setup](/documentation/SensorKit#Setup)

[

Configuring your project for sensor reading](/documentation/sensorkit/configuring-your-project-for-sensor-reading)

Add metadata to your app to attain system and user permission to access sensor data.

```swift
```swift
```swift
class SRSensorReader
```
```

An object that establishes user authorization and records data for a particular sensor.
```

### [Authorization](/documentation/SensorKit#Authorization)

[`com.apple.developer.sensorkit.reader.allow`](/documentation/BundleResources/Entitlements/com.apple.developer.sensorkit.reader.allow)

The necessary entitlement to access sensor data that’s required by your app’s preapproved research study.

### [Querying data](/documentation/SensorKit#Querying-data)

```swift
```swift
```swift
```swift
class SRFetchRequest
```
```

An object that defines the criteria for a sample query.
```
```swift
```swift
```swift
class SRFetchResult
```
```

Recorded data that a sensor reader fetches.
```
```

### [Interpreting data](/documentation/SensorKit#Interpreting-data)

```swift
```swift
```swift
```swift
class SRAmbientLightSample
```
```

The amount of ambient light in the user’s environment.
```
```swift
```swift
```swift
class SRDeviceUsageReport
```
```

The frequency and relative duration that the user uses their device, particular Apple apps, or websites.
```
```swift
```swift
```swift
class SRKeyboardMetrics
```
```

The configuration of a device’s keyboard and its usage patterns.
```
```swift
```swift
```swift
class SRMediaEvent
```
```

A user interaction with a media object, such as an image or a video.
```
```swift
```swift
```swift
class SRMessagesUsageReport
```
```

An object that describes the user’s Messages app activity over a period of time.
```
```swift
```swift
```swift
class SRPhoneUsageReport
```
```

An object that describes the user’s phone activity over a period of time.
```
```swift
```swift
```swift
class SRVisit
```
```

The user’s progress in their daily travel routine.
```
```swift
```swift
```swift
class SRWristDetection
```
```

The configuration of a watch on the wearer’s wrist.
```
```

### [Deleting samples](/documentation/SensorKit#Deleting-samples)

```swift
```swift
```swift
```swift
class SRDeletionRecord
```
```

An object that describes the reason the framework deletes samples.
```
```

### [Analyzing speech](/documentation/SensorKit#Analyzing-speech)

```swift
```swift
```swift
```swift
class SRSpeechMetrics
```
```

An object that represents metrics about a range of speech.
```
```swift
```swift
```swift
class SRSpeechExpression
```
```

An object that represents the metrics and voice analytics for a range of speech.
```
```

### [Analyzing faces](/documentation/SensorKit#Analyzing-faces)

```swift
```swift
```swift
```swift
class SRFaceMetrics
```
```

An object that represents metrics about the user’s face.
```
```swift
```swift
```swift
var SR_ARKIT_SUPPORTED: Int32
```
```

A flag that indicates whether the ARKit framework is available in the SDK for the SensorKit framework.
```
```

### [Recording wrist temperatures](/documentation/SensorKit#Recording-wrist-temperatures)

```swift
```swift
```swift
```swift
class SRWristTemperatureSession
```
```

An object that represents wrist temperatures that a device records during a period of time.
```
```swift
```swift
```swift
class SRWristTemperature
```
```

The temperature of the user’s wrist while the user sleeps.
```
```

### [Recording ectrocardiogram data](/documentation/SensorKit#Recording-ectrocardiogram-data)

```swift
```swift
```swift
```swift
class SRElectrocardiogramSample
```
```

The sample electrocardiogram sensor data.
```
```

### [Recording photoplethysmogram data](/documentation/SensorKit#Recording-photoplethysmogram-data)

```swift
```swift
```swift
```swift
class SRPhotoplethysmogramSample
```
```

The sample photoplethysmogram (PPG) sensor data.
```
```

### [Classes](/documentation/SensorKit#Classes)

```swift
```swift
```swift
```swift
class SRAcousticSettings
```
```
Beta
```
```swift
```swift
```swift
class SRSleepSession
```
```
Beta
```
```