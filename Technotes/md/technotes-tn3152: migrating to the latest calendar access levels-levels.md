

- Technotes
-  TN3152: Migrating to the latest Calendar access levels 

Article

# TN3152: Migrating to the latest Calendar access levels

Follow these guidelines to update your app to use the new Calendar access levels.

## Overview

The EventKit framework brings new Calendar access levels in iOS 17, iPadOS 17, macOS 14, Mac Catalyst 17, watchOS 10, and later. The EventKitUI framework provides the ability to add events without requesting access to Calendar in iOS 17, iPadOS 17, Mac Catalyst 17, and later. See Accessing the Event Store for details. This document describes how to update your app to use these new features. To learn how these changes may affect your existing apps, see TN3153: Adopting API changes for EventKit in iOS 17, macOS 14, and watchOS 10. Follow these guidelines to support the new features:

**Choose the access level needed to complete your tasks.**

- If your app can present EKEventEditViewController to let people create events, don’t request access to events.

- If your app needs to create and save calendar data directly without the user making any later changes, request write-only access to calendar data.

- If accessing existing events is essential to the core experience of your app, request full access to calendar data.

- If your app accesses reminder data, request full access to reminders in your app.

**Build your app with Xcode 15 and link against the SDK matching your app’s platform.** Xcode 15 includes SDKs for iOS 17, macOS 14, and watchOS 10 that provide the new write-only and full access features. For instance, if you are building an iOS app, link your app against the iOS 17 SDK or later. If you are building a watchOS app, link your app against the watchOS 10 SDK or later.

**Replace the calendar usage description keys.** Prior to iOS 17, your app needs to include the NSCalendarsUsageDescription, NSRemindersUsageDescription, and NSContactsUsageDescription keys in its `Info.plist` file before it can access the user’s calendar data or reminders. `NSCalendarsUsageDescription` and `NSRemindersUsageDescription` describe how your app intends to use the user’s calendar data or reminders, respectively. You provide a `NSContactsUsageDescription` key when your app uses EventKit UI to access Contacts data. If your app supports earlier versions of an OS, keep the key currently available in your app’s `Info.plist` file.

If your app requires running on iOS 17, iPadOS 17, macOS 14, Mac Catalyst 17, watchOS 10, or later, remove these keys from the plist file. Add NSCalendarsWriteOnlyAccessUsageDescription or NSCalendarsFullAccessUsageDescription to the plist file, depending on the level of access to events your app needs. Include NSRemindersFullAccessUsageDescription if your app needs access to reminders. See Protect user privacy with information property list keys for details.

**Update the authorization status to handle the writeOnly and fullAccess cases.** If your app checks its authorization status for events EKEventStore.authorizationStatus(for: .event), update it to handle the new writeOnly and fullCase cases. Remove the deprecated authorized case from your app.

**Replace the deprecated request methods.** The iOS, macOS, and watchOS SDKs bundled in Xcode 15 deprecate the requestAccess(to:completion:) and requestAccess(to:) methods. If your app links against the iOS 17 SDK, macOS 14 SDK, or watchOS 10 SDK, calling these deprecated request methods doesn’t prompt the user for access and throws an error message. Remove these methods from your app. Use the new APIs to prompt the user for access in your app:

- To request access to reminders, call requestFullAccessToReminders(completion:) or requestFullAccessToReminders() in your app.

- To request write-only access to events, call requestWriteOnlyAccessToEvents(completion:) or requestWriteOnlyAccessToEvents() in your app.

- To request full access to events, call requestFullAccessToEvents(completion:) or requestFullAccessToEvents() in your app.

See Connect to the event store for details.

## Revision History

- **2023-06-06** First published.

## See Also

### Latest

TN3182: Adding privacy tracking keys to your privacy manifest

Declare the tracking domains you use in your app or third-party SDK in a privacy manifest.

TN3183: Adding required reason API entries to your privacy manifest

Declare the APIs that can potentially fingerprint devices in your app or third-party SDK in a privacy manifest.

TN3184: Adding data collection details to your privacy manifest

Declare the data your app or third-party SDK collects in a privacy manifest.

TN3181: Debugging an invalid privacy manifest

Identify common configurations that cause unsuccessful privacy manifest validation with the App Store.

TN3180: Reverting to App Store Server Notifications V1

Migrate from version 2 to version 1 of App Store Server Notifications using the Modify an App endpoint.

TN3179: Understanding local network privacy

Learn how local network privacy affects your software.

TN3178: Checking for and resolving build UUID problems

Ensure that every Mach-O image has a UUID, and that every distinct Mach-O image has its own unique UUID.

TN3177: Understanding alternate audio track groups in movie files

Learn how alternate groups collect audio tracks, and how to choose which audio track to use in your app.

TN3111: iOS Wi-Fi API overview

Explore the various Wi-Fi APIs available on iOS and their expected use cases.

TN3176: Troubleshooting Apple Pay payment processing issues

Diagnose errors that occur when processing Apple Pay payments, identify common causes, and explore potential solutions.

TN3175: Diagnosing issues with displaying the Apple Pay button on your website

Diagnose common errors received while displaying the Apple Pay button on your website by identifying the underlying causes, and explore potential solutions.

TN3174: Diagnosing issues with the Apple Pay payment sheet on your website

Diagnose errors received while presenting the Apple Pay payment sheet on your website by identifying the underlying causes of common errors and explore their potential solutions.

TN3173: Troubleshooting issues with your Apple Pay merchant identifier configuration

Diagnose errors due to invalid Apple Pay merchant identifier configurations by identifying the underlying causes of common errors and explore their potential solutions.

TN3168: Making your App Clip available in the App Store

Learn how to configure your App Clip to prevent it from being unavailable in the App Store.

TN3124: Debugging coordinate space issues

Learn techniques to help debug any coordinate space issue.

