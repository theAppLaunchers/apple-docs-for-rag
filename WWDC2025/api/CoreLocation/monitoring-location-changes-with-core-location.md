*   [Core Location](/documentation/corelocation)
*   Monitoring location changes with Core Location

Sample Code

# Monitoring location changes with Core Location

Define boundaries and act on user location updates.

[Download](https://docs-assets.developer.apple.com/published/60d004152b62/MonitoringLocationChangesWithCoreLocation.zip)

iOS 18.0+iPadOS 18.0+Xcode 15.3+

## [Overview](/documentation/CoreLocation/monitoring-location-changes-with-core-location#Overview)

Note

This sample code project is associated with WWDC24 session 10212: [What’s new in location authorization](https://developer.apple.com/wwdc24/10212/) and WWDC23 session 10147: [Meet Core Location Monitor](https://developer.apple.com/wwdc23/10147/).

### [Configure the sample code project](/documentation/CoreLocation/monitoring-location-changes-with-core-location#Configure-the-sample-code-project)

Before you run the sample code project in Xcode, ensure that you’re using Xcode 16 or later and iOS 18 or later.

## [See Also](/documentation/CoreLocation/monitoring-location-changes-with-core-location#see-also)

### [Essentials](/documentation/CoreLocation/monitoring-location-changes-with-core-location#Essentials)

[

Configuring your app to use location services](/documentation/corelocation/configuring-your-app-to-use-location-services)

Prepare your app to start collecting location data.

[

Supporting live updates in SwiftUI and Mac Catalyst apps](/documentation/corelocation/supporting-live-updates-in-swiftui-and-mac-catalyst-apps)

Enable background events by adding lifecycle event support.

```swift
```swift
```swift
class CLLocationManager
```
```

The object you use to start and stop the delivery of location-related events to your app.
```
```swift
```swift
```swift
class CLBackgroundActivitySession
```
```

An object that manages a visual indicator that keeps your app in use in the background, allowing it to receive updates or events.
```
```swift
```swift
```swift
struct CLLocationUpdate
```
```

A structure that contains the location information the framework delivers with each update.
```

[

Adopting live updates in Core Location](/documentation/corelocation/adopting-live-updates-in-core-location)

Simplify location delivery using asynchronous events in Swift.