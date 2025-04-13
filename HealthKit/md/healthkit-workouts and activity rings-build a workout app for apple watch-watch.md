

- HealthKit
- Workouts and activity rings
-  Build a workout app for Apple Watch 

Sample Code

# Build a workout app for Apple Watch

Create your own workout app, quickly and easily, with HealthKit and SwiftUI.

Download

iOS 15.0+iPadOS 15.0+watchOS 8.0+Xcode 14.2+

## Overview

Note

This sample code project is associated with WWDC21 session 10009: Build a workout app for Apple Watch.

### Configure the sample code project

Before you run the sample code project in Xcode:

1.  Open the sample with the latest version of Xcode.

2.  Select the top-level project.

3.  For the three targets, select the correct team in the Signing & Capabilities pane (next to Team) to let Xcode automatically manage your provisioning profile.

4.  Make a note of the Bundle Identifier of the WatchKit App target.

5.  Open the `Info.plist` file of the WatchKit Extension target, and change the value of the `NSExtension` \> `NSExtensionAttributes` \> `WKAppBundleIdentifier` key to the bundle ID you noted in the previous step.

6.  Make a clean build and run the sample app on your device.

## See Also

### Sessions

Running workout sessions

Track a workout on Apple Watch.

Building a multidevice workout app

Mirror a workout from a watchOS app to its companion iOS app, and perform bidirectional communication between them.

class HKWorkoutSession

A session that tracks the user’s workout on Apple Watch.

class HKWorkoutConfiguration

An object that contains configuration information about a workout session.

enum HKWorkoutSessionState

A workout session’s state.

class HKLiveWorkoutBuilder

A builder object that constructs a workout incrementally based on live data from an active workout session.

class HKLiveWorkoutDataSource

A data source that automatically provides live data from an active workout session.

