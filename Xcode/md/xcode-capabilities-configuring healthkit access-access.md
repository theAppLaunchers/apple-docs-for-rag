

- Xcode
- Capabilities
-  Configuring HealthKit access 

Article

# Configuring HealthKit access

Read and write health and activity data in the Health app.

## Overview

HealthKit is the central repository for health and fitness data in iOS and watchOS. Health apps that integrate with HealthKit can request a user’s permission to both read health data from and write data to this central repository. The data your app writes to the HealthKit store is visible to the user in the Health app, alongside their other health-related data.

To enable your app to access the user’s HealthKit store, you must add the HealthKit capability to your app’s target and include a short description of the app’s functionality in its target’s `Info.plist` file.

### Add the HealthKit capability to your target

Follow the steps in Add a capability to add the capability to your app’s target; be sure to select the HealthKit capability from Xcode’s Capabilities library. For watchOS apps with separate WatchKit extensions, you must add the capability to the WatchKit Extension target.

Note

The HealthKit capability is available for iOS and watchOS apps. watchOS apps can only access certain health data. Clinical Health Records aren’t accessible by watchOS apps.

After you add the HealthKit capability, Xcode links the HealthKit framework to your target and updates the target’s entitlements file to include the HealthKit Entitlement. If Xcode automatically manages the signing of your app, it also enables HealthKit for your app’s App ID.

Note

If you later remove the HealthKit capability in Xcode, you must manually update your App ID’s configuration in your developer account to disable HealthKit.

### Request access to the user’s health data

HealthKit uses a fine-grained authorization mechanism to help protect the user’s privacy; your app must request permission to read and, optionally, write each individual sample type it supports. For more information, see Authorizing access to health data.

Before prompting the user for their permission, you must configure your app to include one or more *purpose strings*, which accurately and concisely describe why the app needs to read the user’s health data, write health data to their HealthKit store, or both. The presence of these purpose strings is an App Store requirement for any app that integrates with HealthKit. The system displays this information to the user when requesting their permission, along with the specific sample types that your app needs to access, which helps them make an informed decision.

Follow these steps to add the purpose string for reading health data to your app’s target:

1.  In the Project navigator, select your target’s `Info.plist` file.

2.  Move the mouse pointer over the “Information Property List” key.

3.  Click the Add button (+) that appears.

4.  Choose “Privacy - Health Share Usage Description”.

5.  Double-click the Value column to the right of the key and enter your app’s purpose string.

If your app writes health data to the HealthKit store, repeat the steps above and add the “Privacy - Health Update Usage Description” key.

Remember that the user can revoke their permission at any time in the Settings app or the Health app. If your app requires access to certain health data, you must clearly display information about why your app requires access to the user’s health data and request that the user reauthorize to grant your app access to the HealthKit data.

You can check your app’s current authorization status using the authorizationStatus(for:) method. HealthKit also returns a HKError.Code.errorAuthorizationDenied error if your app attempts unauthorized access to the user’s health data.

### Request access to a user’s health records

HealthKit’s clinical-record support allows users to download their records in the Fast Healthcare Interoperability Resources (FHIR) format from supported healthcare institutions. HealthKit then periodically updates those records in the background.

Due to the sensitive nature of health records, your app requires a special entitlement before it can access them. Follow these steps to configure that entitlement:

1.  Select your project in Xcode’s Project navigator.

2.  Select your app’s target from the Targets list.

3.  Click the Signing & Capabilities tab in the project editor.

4.  Find the HealthKit capability.

5.  Enable the nested Clinical Health Records capability.

Xcode adds the HealthKit Capabilities Entitlement to your target’s entitlements file and appends the `health-records` value to the array it contains.

After you enable the capability, there are additional configuration steps you must complete before your app can access the user’s health records, such as providing an additional purpose string and declaring the types of health records that your app supports. For more information, see Accessing Health Records.

### Receive sample updates in the background

HealthKit observer queries are long-running ones that watch the HealthKit store for changes to specific sample types and deliver those changes to your app on a background thread. Typically, observer queries only provide those changes when your app is running in the foreground.

However, by enabling Background Delivery, your app can continue to receive and process changes while it’s in the background. You pair each executed observer query with a call to enableBackgroundDelivery(for:frequency:withCompletion:) and specify the same sample type. The system then wakes your app when changes occur in the HealthKit store — at most, once per the update frequency you specify — and delivers those changes to the corresponding observer queries. For more information, see Executing Observer Queries.

To enable HealthKit to continue updating your app’s observer queries while its in the background, perform the following:

1.  Select your project in Xcode’s Project navigator.

2.  Select the app’s target from the Targets list.

3.  Click the Signing & Capabilities tab in the project editor.

4.  Find the HealthKit capability.

5.  Enable the nested Background Delivery capability.

Xcode adds the com.apple.developer.healthkit.background-delivery entitlement to the target’s entitlements file.

## See Also

### User data

Configuring HomeKit access

Discover compatible accessories and communicate with configured accessories and services to perform actions.

