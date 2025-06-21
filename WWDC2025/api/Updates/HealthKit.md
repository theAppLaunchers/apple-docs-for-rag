*   [Updates](/documentation/updates)
*   HealthKit updates

Article

# HealthKit updates

Learn about important changes to HealthKit.

## [Overview](/documentation/Updates/HealthKit#Overview)

Browse notable changes in [HealthKit](/documentation/HealthKit).

## [June 2025](/documentation/Updates/HealthKit#June-2025)

*   Start workout sessions on iOS using [`HKLiveWorkoutBuilder`](/documentation/HealthKit/HKLiveWorkoutBuilder).
    
*   Query medications that a person has added to the Health app, using [`HKUserAnnotatedMedicationQueryDescriptor`](/documentation/HealthKit/HKUserAnnotatedMedicationQueryDescriptor) and the times they’ve logged that medication using [`HKMedicationDoseEventType`](/documentation/HealthKit/HKMedicationDoseEventType).
    

## [September 2024](/documentation/Updates/HealthKit#September-2024)

*   Apple Watch Series 10 supports the Shallow Depth and Pressure capability. Use [`underwaterDepth`](/documentation/HealthKit/HKQuantityTypeIdentifier/underwaterDepth) and [`waterTemperature`](/documentation/HealthKit/HKQuantityTypeIdentifier/waterTemperature) to read depth and temperature data from shallow dives.
    

## [June 2024](/documentation/Updates/HealthKit#June-2024)

### [General](/documentation/Updates/HealthKit#General)

*   Create HealthKit apps for VisionOS.
    
*   Associate perceived and estimated exertion values with workouts. Use [`workoutEffortScore`](/documentation/HealthKit/HKQuantityTypeIdentifier/workoutEffortScore) and [`estimatedWorkoutEffortScore`](/documentation/HealthKit/HKQuantityTypeIdentifier/estimatedWorkoutEffortScore) to read and write exertion data. Use [`relateWorkoutEffortSample(_:with:activity:completion:)`](/documentation/HealthKit/HKHealthStore/relateWorkoutEffortSample\(_:with:activity:completion:\)) to associate exertion data with a workout, and [`HKWorkoutEffortRelationshipQuery`](/documentation/HealthKit/HKWorkoutEffortRelationshipQuery) to query for associated exertion data.
    
*   Access water temperature data from swimming workouts. Any Apple Watch Ultra records [`waterTemperature`](/documentation/HealthKit/HKQuantityTypeIdentifier/waterTemperature) samples during swimming workouts.
    
*   Read and write mental well-being samples using the [`HKStateOfMind`](/documentation/HealthKit/HKStateOfMind), [`HKPHQ9Assessment`](/documentation/HealthKit/HKPHQ9Assessment), and [`HKGAD7Assessment`](/documentation/HealthKit/HKGAD7Assessment) data types.
    
*   Track menstrual flow and intermenstrual bleeding during pregnancy using the [`bleedingDuringPregnancy`](/documentation/HealthKit/HKCategoryTypeIdentifier/bleedingDuringPregnancy) and [`bleedingAfterPregnancy`](/documentation/HealthKit/HKCategoryTypeIdentifier/bleedingAfterPregnancy) data types.
    

### [June 2023](/documentation/Updates/HealthKit#June-2023)

*   Now available in iPadOS. Health data automatically synchronizes between a person’s iPhone, iPad, and Apple Watch.
    
*   Create custom, interval-based workouts. You can use either distance or time for the intervals, and sync the intervals to a group, such as a workout class.
    
*   Mirror workout sessions in your iOS app. This includes the ability to control the workout session from the iOS app, and the ability to send data between the iOS and watchOS apps during an active workout session.
    
*   Access batches of higher-rate motion data from Apple Watch. New Core Motion APIs provide 800 Hz accelerometer data and 200 Hz device motion data. Use this data to analyze someone’s motion after performing an action, like swinging a golf club.
    
*   Measure time spent outdoors and average light intensity with new data types.
    
*   Track cycling with new data types for tracking someone’s power, speed, cadence, and functional threshold power.
    

## [See Also](/documentation/Updates/HealthKit#see-also)

### [Technology updates](/documentation/Updates/HealthKit#Technology-updates)

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