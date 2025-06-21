Framework

# Core Location

Obtain the geographic location and orientation of a device.

iOS 2.0+iPadOS 2.0+Mac Catalyst 13.0+macOS 10.6+tvOS 9.0+visionOS 1.0+watchOS 2.0+

## [Overview](/documentation/CoreLocation#overview)

Core Location provides services that determine a device’s geographic location, altitude, and orientation, or its position relative to a nearby iBeacon device. The framework gathers data using all available components on the device, including the Wi-Fi, GPS, Bluetooth, magnetometer, barometer, and cellular hardware.

You use instances of the [`CLLocationManager`](/documentation/corelocation/cllocationmanager) class to configure, start, and stop the Core Location services. A location manager object supports the following location-related activities:

Standard and significant location updates

Track large or small changes in the user’s current location with a configurable degree of accuracy.

Region monitoring

Monitor distinct regions of interest and generate location events when the user enters or leaves those regions.

Beacon ranging

Detect and locate nearby beacons.

Compass headings

Report heading changes from the onboard compass.

To use location services, call [`liveUpdates(_:)`](/documentation/corelocation/cllocationupdate/liveupdates\(_:\)) to obtain an update stream, then asynchronously iterate over that stream to receive and process location updates, and receive diagnostic properties to understand if and why location updates don’t arrive.

If needed, the system prompts the user to grant or deny the request. An initial prompt is shown in the example below:

![A screenshot of an iPhone showing a prompt asking the user if they allow the “Park Finder” app to have access to their location. The options are “OK” and “Not now”.](https://docs-assets.developer.apple.com/published/71e6a0fc9cb93b0e6926165d35fc2b16/core-location-overview%402x.png)

On iOS devices, users can change location service settings at any time in the Settings app, affecting individual apps or the device as a whole. Your app receives events, including authorization changes, by observing asynchronous sequences from [`CLLocationUpdate`](/documentation/corelocation/cllocationupdate) and [`CLMonitor`](/documentation/corelocation/clmonitor-6ynwz).

## [Topics](/documentation/CoreLocation#topics)

### [Essentials](/documentation/CoreLocation#Essentials)

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

[

Monitoring location changes with Core Location](/documentation/corelocation/monitoring-location-changes-with-core-location)

Define boundaries and act on user location updates.

### [Authorization](/documentation/CoreLocation#Authorization)

[

Requesting authorization to use location services](/documentation/corelocation/requesting-authorization-to-use-location-services)

Obtain authorization to use location services and manage changes to your app’s authorization status.

[

Suspending authorization requests](/documentation/corelocation/suspending-authorization-requests)

Defer the system’s authorization request dialog until your app is ready.

```swift
```swift
```swift
enum CLAuthorizationStatus
```
```

Constants that indicate the app’s authorization to use location services.
```
```swift
```swift
```swift
enum CLAccuracyAuthorization
```
```

Constants that indicate the level of location accuracy the app has authorization to use.
```

[`NSLocationAlwaysAndWhenInUseUsageDescription`](/documentation/BundleResources/Information-Property-List/NSLocationAlwaysAndWhenInUseUsageDescription)

A message that tells the user why the app is requesting access to the user’s location information at all times.

[`NSLocationWhenInUseUsageDescription`](/documentation/BundleResources/Information-Property-List/NSLocationWhenInUseUsageDescription)

A message that tells the user why the app is requesting access to the user’s location information while the app is running in the foreground.

[`NSLocationUsageDescription`](/documentation/BundleResources/Information-Property-List/NSLocationUsageDescription)

A message that tells the user why the app is requesting access to the user’s location information.

Deprecated

[`NSLocationDefaultAccuracyReduced`](/documentation/BundleResources/Information-Property-List/NSLocationDefaultAccuracyReduced)

A Boolean value that indicates whether the app requests reduced location accuracy by default.

[`NSLocationAlwaysUsageDescription`](/documentation/BundleResources/Information-Property-List/NSLocationAlwaysUsageDescription)

A message that tells the user why the app is requesting access to the user’s location at all times.

Deprecated

### [Monitoring](/documentation/CoreLocation#Monitoring)

[`actor CLMonitor`](/documentation/corelocation/clmonitor-2r51v)

An object that monitors the conditions you add to it.

### [Location updates](/documentation/CoreLocation#Location-updates)

[

Getting the current location of a device](/documentation/corelocation/getting-the-current-location-of-a-device)

Start location services and provide information the system needs to optimize power usage for those services.

[

Handling location updates in the background](/documentation/corelocation/handling-location-updates-in-the-background)

Configure your app to receive location updates when it isn’t running in the foreground.

[

Creating a location push service extension](/documentation/corelocation/creating-a-location-push-service-extension)

Add and configure an extension to enable your location-sharing app to access a user’s location in response to a request from another user.

```swift
```swift
```swift
class CLVisit
```
```

Information about the user’s location during a specific period of time.
```

[

Monitoring location changes with Core Location](/documentation/corelocation/monitoring-location-changes-with-core-location)

Define boundaries and act on user location updates.

```swift
```swift
```swift
class CLServiceSession
```
```
```

### [Region monitoring](/documentation/CoreLocation#Region-monitoring)

Configure geofences and receive notifications when the user’s device crosses the fence’s boundaries.

[

Monitoring the user’s proximity to geographic regions](/documentation/corelocation/monitoring-the-user-s-proximity-to-geographic-regions)

Use condition monitoring to determine when the user enters or leaves a geographic region.

```swift
```swift
```swift
class CLRegion
```
```

A base class representing an area that can be monitored.
```

### [iBeacon](/documentation/CoreLocation#iBeacon)

[

Ranging for Beacons](/documentation/corelocation/ranging-for-beacons)

Configure a device to act as a beacon and to detect surrounding beacons.

[

Determining the proximity to an iBeacon device](/documentation/corelocation/determining-the-proximity-to-an-ibeacon-device)

Detect beacons and determine the relative distance to them.

[

Turning an iOS device into an iBeacon device](/documentation/corelocation/turning-an-ios-device-into-an-ibeacon-device)

Broadcast iBeacon signals from an iOS device.

```swift
```swift
```swift
class CLBeacon
```
```

Information about an observed iBeacon device and its relative distance to a person’s device.
```
```swift
```swift
```swift
protocol CLCondition
```
```

The abstract base class for all other monitor conditions.
```

### [Compass headings](/documentation/CoreLocation#Compass-headings)

Determine the device’s orientation relative to magnetic or true north.

[

Getting heading and course information](/documentation/corelocation/getting-heading-and-course-information)

Use a device’s orientation and course information for navigation.

```swift
```swift
```swift
class CLHeading
```
```

The orientation of the user’s device, relative to true or magnetic north.
```

### [Geocoding](/documentation/CoreLocation#Geocoding)

[

Converting between coordinates and user-friendly place names](/documentation/corelocation/converting-between-coordinates-and-user-friendly-place-names)

Convert between a latitude and longitude pair and a more user-friendly description of that location.

[

Converting a user’s location to a descriptive placemark](/documentation/corelocation/converting-a-user-s-location-to-a-descriptive-placemark)

Transform the user’s location that displays on a map into an informative textual description by reverse geocoding.

```swift
```swift
```swift
class CLGeocoder
```
```

An interface for converting between geographic coordinates and place names.

Deprecated
```
```swift
```swift
```swift
class CLPlacemark
```
```

A user-friendly description of a geographic coordinate, often containing the name of the place, its address, and other relevant information.

Deprecated
```

### [Location push service extension](/documentation/CoreLocation#Location-push-service-extension)

[`com.apple.developer.location.push`](/documentation/BundleResources/Entitlements/com.apple.developer.location.push)

An entitlement to enable a location-sharing app to query someone’s location in response to a push notification.

```swift
```swift
```swift
protocol CLLocationPushServiceExtension
```
```

The interface you adopt in the type that acts as the main entry point for a Location Push Service Extension.
```
```swift
```swift
```swift
struct CLLocationPushServiceError
```
```

Error codes the location manager returns if starting to monitor for location push notifications fails.
```
```swift
```swift
```swift
let CLLocationPushServiceErrorDomain: String
```
```

The domain for Location Push Service Extension errors.
```
```swift
```swift
```swift
enum Code
```
```

Error codes the location manager returns if starting to monitor for location push notifications fails.
```

### [Errors](/documentation/CoreLocation#Errors)

```swift
```swift
```swift
```swift
struct CLError
```
```

A Core Location error.
```
```swift
```swift
```swift
let kCLErrorDomain: String
```
```

The domain for Core Location errors.
```
```swift
```swift
```swift
let kCLErrorUserInfoAlternateRegionKey: String
```
```

A key in the user information dictionary of an error relating to a delayed region-monitoring response.
```
```

### [Deprecated](/documentation/CoreLocation#Deprecated)

[

API Reference

Deprecated](/documentation/corelocation/deprecated)

### [Reference](/documentation/CoreLocation#Reference)

[

API Reference

Core Location Constants](/documentation/corelocation/core-location-constants)

This document describes the constants found in the Core Location framework.

[

API Reference

Core Location Functions](/documentation/corelocation/core-location-functions)

The Core Location framework provides functions to help you work with coordinate values.