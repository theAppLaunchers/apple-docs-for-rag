*   [Updates](/documentation/updates)
*   watchOS updates

Article

# watchOS updates

Learn about important changes to watchOS.

## [Overview](/documentation/Updates/watchos#Overview)

Browse notable changes in [watchOS apps](/documentation/watchOS-Apps).

## [September 2024](/documentation/Updates/watchos#September-2024)

### [Watch sizes](/documentation/Updates/watchos#Watch-sizes)

*   Apple Watch Series 10 are larger and have a different aspect ratio than previous watches. The watch is 1mm larger than the Series 9 (42mm and 46mm), but the screen gains more width than height. Use [`scenePadding(_:)`](/documentation/SwiftUI/View/scenePadding\(_:\)) to align text with the text margins, and [`ignoresSafeArea(_:edges:)`](/documentation/SwiftUI/View/ignoresSafeArea\(_:edges:\)) to extend content beyond the watch’s safe area.
    

### [Shallow dives](/documentation/Updates/watchos#Shallow-dives)

*   Apple Watch Series 10 supports the Shallow Depth and Pressure capability. Use [`CMWaterSubmersionManager`](/documentation/CoreMotion/CMWaterSubmersionManager) to start a shallow dive session, and [`underwaterDepth`](/documentation/HealthKit/HKQuantityTypeIdentifier/underwaterDepth) and [`waterTemperature`](/documentation/HealthKit/HKQuantityTypeIdentifier/waterTemperature) to read depth and temperature samples from HealthKit.
    

## [June 2024](/documentation/Updates/watchos#June-2024)

### [Water temperature](/documentation/Updates/watchos#Water-temperature)

*   Access water temperature data from swimming workouts. Apple Watch Ultra records [`waterTemperature`](/documentation/HealthKit/HKQuantityTypeIdentifier/waterTemperature) samples during swimming workouts.
    

### [Double tap](/documentation/Updates/watchos#Double-tap)

*   Specify which control responds to the double tap gesture using the [`handGestureShortcut(_:isEnabled:)`](/documentation/SwiftUI/View/handGestureShortcut\(_:isEnabled:\)) view modifier, passing [`primaryAction`](/documentation/SwiftUI/HandGestureShortcut/primaryAction) as the parameter. Double tap can interact with any buttonlike controls, such as buttons or toggles.
    

### [Creating workouts](/documentation/Updates/watchos#Creating-workouts)

*   Create custom pool swimming workouts with the [`HKWorkoutActivityType.swimming`](/documentation/HealthKit/HKWorkoutActivityType/swimming) activity.
    
*   Set a distance-with-time goal for custom swimming workouts with the [`WorkoutGoal.poolSwimDistanceWithTime(_:_:)`](/documentation/WorkoutKit/WorkoutGoal/poolSwimDistanceWithTime\(_:_:\)) goal.
    
*   Provide a custom name to a workout step using the [`WorkoutStep`](/documentation/WorkoutKit/WorkoutStep) structure’s [`displayName`](/documentation/WorkoutKit/WorkoutStep/displayName).
    
*   Preview workouts on Apple Watch using the [`workoutPreview(_:isPresented:)`](/documentation/SwiftUI/View/workoutPreview\(_:isPresented:\)) view modifier.
    
*   Set average power goals for cycling and running with [`PowerThresholdAlert`](/documentation/WorkoutKit/PowerThresholdAlert) and [`PowerRangeAlert`](/documentation/WorkoutKit/PowerRangeAlert).
    
*   Set pace goals for indoor running with the [`SpeedThresholdAlert`](/documentation/WorkoutKit/SpeedThresholdAlert) and [`SpeedRangeAlert`](/documentation/WorkoutKit/SpeedRangeAlert) targets.
    

## [September 2023](/documentation/Updates/watchos#September-2023)

*   When someone performs a Double Tap gesture while viewing a notification on Apple Watch Series 9 or Apple Watch Ultra 2, the system invokes the first nondestructive action. A nondestructive action doesn’t include the [`destructive`](/documentation/UserNotifications/UNNotificationActionOptions/destructive) option, and won’t delete user data or change the app irrevocably.
    

## [June 2023](/documentation/Updates/watchos#June-2023)

*   Use the new watchOS user interface design to simplify navigation, better use the Digital Crown, and enrich the app experience. For more information, see [Designing for watchOS](/design/Human-Interface-Guidelines/designing-for-watchos) and [Creating an intuitive and effective UI in watchOS 10](/documentation/watchOS-Apps/creating-an-intuitive-and-effective-ui-in-watchos-10).
    
*   Update your WidgetKit-based complications to take advantage of the Smart Stack on Apple Watch. People can scroll down to see relevant widgets directly on the watch face using the Digital Crown. For more information, see [Increasing the visibility of widgets in Smart Stacks](/documentation/WidgetKit/Widget-Suggestions-In-Smart-Stacks).
    
*   Use curved text along the bevel or around the corners in WidgetKit-based complications.
    
*   Add state preservation and restoration to watchOS apps. For more information, see [Preserving your app’s UI across launches](/documentation/UIKit/preserving-your-app-s-ui-across-launches).
    
*   Use WorkoutKit to create goal, pacer, multisport, and fully custom interval workouts. Display a preview of the workout that shows the workout details, and sync workouts with a paired Apple Watch. For more information, see [WorkoutKit](/documentation/WorkoutKit).
    
*   Access batches of high-frequency accelerometer and device motion data during workouts. Use this data to analyze motion — such as a golf or baseball swing — after the action occurs. For more information, see [Core Motion](/documentation/CoreMotion).
    
*   Use Core Motion’s water submersion manager to monitor shallow dives on Apple Watch Ultra. For more information, see [Core Motion](/documentation/CoreMotion).
    
*   Support Bluetooth cycling sensors. People can pair power, cadence, and speed sensors to Apple Watch to enhance their cycling workouts. You can access this data using HealthKit for live and historical workouts.
    

## [See Also](/documentation/Updates/watchos#see-also)

### [Technology updates](/documentation/Updates/watchos#Technology-updates)

[

Accelerate updates](/documentation/updates/accelerate)

Learn about important changes to Accelerate.

[

Accessibility updates](/documentation/updates/accessibility)

Learn about important changes to Accessibility.

[

ActivityKit updates](/documentation/updates/activitykit)

Learn about important changes in ActivityKit.

[

AdAttributionKit Updates](/documentation/updates/adattributionkit)

Learn about important changes to AdAttributionKit.

[

App Clips updates](/documentation/updates/appclips)

Learn about important changes in App Clips.

[

App Intents updates](/documentation/updates/appintents)

Learn about important changes in App Intents.

[

AppKit updates](/documentation/updates/appkit)

Learn about important changes to AppKit.

[

Apple Intelligence updates](/documentation/updates/apple-intelligence)

Learn about important changes to Apple Intelligence.

[

AppleMapsServerAPI Updates](/documentation/updates/applemapsserverapi)

Learn about important changes to AppleMapsServerAPI.

[

Apple Pencil updates](/documentation/updates/applepencil)

Learn about important changes to Apple Pencil.

[

ARKit updates](/documentation/updates/arkit)

Learn about important changes to ARKit.

[

Audio Toolbox updates](/documentation/updates/audiotoolbox)

Learn about important changes to Audio Toolbox.

[

AuthenticationServices updates](/documentation/updates/authenticationservices)

Learn about important changes to AuthenticationServices.

[

AVFAudio updates](/documentation/updates/avfaudio)

Learn about important changes to AVFAudio.

[

AVFoundation updates](/documentation/updates/avfoundation)

Learn about important changes to AVFoundation.