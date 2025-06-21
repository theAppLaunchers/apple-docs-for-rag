Framework

# DeviceActivity

Monitor device activity with your app extension while maintaining user privacy.

iOS 15.0+iPadOS 15.0+Mac Catalyst 15.0+

## [Overview](/documentation/DeviceActivity#overview)

Device Activity provides a privacy-preserving way for an application to monitor a user’s application and website activity. For instance, you can set up a bedtime schedule that monitors device activity while the user is supposed to be asleep. Your app extension can receive warnings before an activity’s schedule starts or ends, or when an activity is about to reach a predefined threshold. You can monitor the time spent on websites and apps to warn the user once they have reached their threshold.

![A diagram depicting different kinds of device activity the framework can monitor. On the left are three icons in a vertical row, including an App store icon, a Settings icon, and a Safari icon. All three icons have arrows pointing to a clock.](https://docs-assets.developer.apple.com/published/c79b787bbcf2be82c54de00a0ec7610c/device-activity-overview%402x.png)

## [Topics](/documentation/DeviceActivity#topics)

### [Manage Activities](/documentation/DeviceActivity#Manage-Activities)

```swift
```swift
```swift
```swift
struct DeviceActivityEvent
```
```

An event that represents an application, category, or website activity.
```
```swift
```swift
```swift
struct DeviceActivityName
```
```

The unique name of an activity.
```
```swift
```swift
```swift
struct DeviceActivitySchedule
```
```

A calendar-based schedule for when to monitor a device’s activity.
```
```swift
```swift
```swift
struct DeviceActivityCenter
```
```

A class that enables an application’s extension to start monitoring scheduled device activity.
```
```

### [Monitor Activity](/documentation/DeviceActivity#Monitor-Activity)

```swift
```swift
```swift
```swift
class DeviceActivityMonitor
```
```

The object that monitors scheduled device activity.
```
```

### [Errors](/documentation/DeviceActivity#Errors)

```swift
```swift
```swift
```swift
enum MonitoringError
```
```

Errors that may occur when starting to monitor an activity.
```
```

### [Classes](/documentation/DeviceActivity#Classes)

```swift
```swift
```swift
```swift
class DeviceActivityAuthorization
```
```
```
```

### [Protocols](/documentation/DeviceActivity#Protocols)

```swift
```swift
```swift
```swift
protocol DeviceActivityAuthorizing
```
```
```
```swift
```swift
```swift
protocol DeviceActivityReportExtension
```
```

An app extension that reports device activity data.
```
```swift
```swift
```swift
protocol DeviceActivityReportScene
```
```

Defines a custom device activity report scene.
```
```

### [Structures](/documentation/DeviceActivity#Structures)

```swift
```swift
```swift
```swift
struct DeviceActivityData
```
```

Represents the activity of a [`DeviceActivityData.User`](/documentation/deviceactivity/deviceactivitydata/user-swift.struct) on a particular [`DeviceActivityData.Device`](/documentation/deviceactivity/deviceactivitydata/device-swift.struct).
```
```swift
```swift
```swift
struct DeviceActivityFilter
```
```

A type that filters the device activity data to include in a report.
```
```swift
```swift
```swift
struct DeviceActivityReport
```
```

A view that reports the user’s application, category, and web domain activity in a privacy-preserving way.
```
```swift
```swift
```swift
struct DeviceActivityReportBuilder
```
```

A result builder that combines one or more `DeviceActivityReportScene`s into a single scene.
```
```swift
```swift
```swift
struct DeviceActivityResults
```
```

An asynchronous sequence of filtered device activity results.
```
```