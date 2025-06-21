Framework

# Exposure Notification

Implement a COVID-19 exposure notification system that protects user privacy.

iOS 13.5+iPadOS 13.5+Mac Catalyst 13.5+

## [Overview](/documentation/ExposureNotification#overview)

Use the Exposure Notification framework to inform people of potential exposure to COVID-19, the disease caused by the SARS-CoV-2 virus. You can build a notification system that employs random, rotating keys and identifiers to convey positive diagnoses in addition to data such as associated symptoms, proximity, and duration.

### [Establish User Roles](/documentation/ExposureNotification#Establish-User-Roles)

The ExposureNotification framework defines two user roles:

Affected user

When a user has a confirmed or probable diagnosis of COVID-19 (as defined by the Health Authority), the framework identifies them as _affected_ and shares their diagnosis keys to alert other users to potential exposure.

Potentially exposed user

To assign a user the _potentially exposed_ role, use the framework to determine whether a set of temporary exposure keys indicate proximity to an affected user. If so, the app can retrieve additional information such as date and duration from the framework.

Important

Before you can develop an app that uses ExposureNotification, you need the [`com.apple.developer.exposure-notification`](/documentation/BundleResources/Entitlements/com.apple.developer.exposure-notification) entitlement. For more information on this entitlement, see [Exposure Notification APIs Addendum](https://developer.apple.com/contact/request/download/Exposure_Notification_Addendum.pdf). To get permission to use this entitlement, see [Exposure Notification Entitlement Request](https://developer.apple.com/contact/request/exposure-notification-entitlement).

### [Identify Your App’s Region](/documentation/ExposureNotification#Identify-Your-Apps-Region)

All EN apps must specify the region for which they work by adding a key called [`ENDeveloperRegion`](/documentation/BundleResources/Information-Property-List/ENDeveloperRegion) to the app’s `Info.plist` file. The value for `ENDeveloperRegion` is set to a string that represents the app’s region. This value can be an ISO 3166-1 country code (for example, “CA” for Canada), or the ISO 3166-1/3166-2 country code plus subdivision code (“US-CA” for California).

Explicitly set the associated domain link to your region code. Avoid using wildcards because they can impact system operations. See [`Associated Domains Entitlement`](/documentation/BundleResources/Entitlements/com.apple.developer.associated-domains) for more information.

### [Specify Exposure Notification API Version](/documentation/ExposureNotification#Specify-Exposure-Notification-API-Version)

iOS 13.7 introduces a new method of calculating the user’s Exposure Risk Value, described in [`ENExposureConfiguration`](/documentation/exposurenotification/enexposureconfiguration). Apps can implement this new method, or continue to use the calculation method introduced in earlier versions of iOS. To choose your app’s approach, add an entry to your app’s `Info.plist` file with a key of [`ENAPIVersion`](/documentation/BundleResources/Information-Property-List/ENAPIVersion). To use the new approach, specify a value of `2`. To use the original approach, specify a value of `1`.

### [Support Exposure Notification Express](/documentation/ExposureNotification#Support-Exposure-Notification-Express)

Starting with iOS 13.7, Health Authorities can inform users of potential exposure to COVID-19 without a dedicated Exposure Notification app. This feature is called Exposure Notification Express and must be enabled by a Health Authority. For more information, see [Supporting Exposure Notifications Express](/documentation/exposurenotification/supporting-exposure-notifications-express).

## [Topics](/documentation/ExposureNotification#topics)

### [Essentials](/documentation/ExposureNotification#Essentials)

[

API Reference

Supporting Exposure Notifications Express](/documentation/exposurenotification/supporting-exposure-notifications-express)

Configure servers to notify users of potential exposures to COVID-19 without an app.

[

Building an App to Notify Users of COVID-19 Exposure](/documentation/exposurenotification/building-an-app-to-notify-users-of-covid-19-exposure)

Inform people when they may have been exposed to COVID-19.

[

Setting Up a Key Server](/documentation/exposurenotification/setting-up-a-key-server)

Ensure that your server meets the requirements for supporting Exposure Notifications.

```swift
```swift
```swift
class ENManager
```
```

A class that manages exposure notifications.
```

[`ENDeveloperRegion`](/documentation/BundleResources/Information-Property-List/ENDeveloperRegion)

A string that specifies the region that the app supports.

[`ENAPIVersion`](/documentation/BundleResources/Information-Property-List/ENAPIVersion)

A number that specifies the version of the API to use.

[

Changing Configuration Values Using the Server‑to‑Server API](/documentation/exposurenotification/changing-configuration-values-using-the-server-to-server-api)

Update Exposure Notifications configuration values from a Public Health Authority’s server.

[

Testing Exposure Notifications Apps in iOS 13.7 and Later](/documentation/exposurenotification/testing-exposure-notifications-apps-in-ios-13-7-and-later)

Perform end-to-end validation of Exposure Notifications apps on a device by manually loading configuration files.

[

Supporting Exposure Notifications in iOS 12.5](/documentation/exposurenotification/supporting-exposure-notifications-in-ios-12-5)

Prepare your Exposure Notifications app to run on a previous version of iOS.

### [Exposures](/documentation/ExposureNotification#Exposures)

[

Configuring Exposure Notifications](/documentation/exposurenotification/configuring-exposure-notifications)

Define how Exposure Notifications work for a region by assigning server-based key-value pairs.

```swift
```swift
```swift
class ENExposureConfiguration
```
```

The object that contains parameters for configuring exposure notification risk scoring behavior.
```
```swift
```swift
```swift
class ENExposureWindow
```
```

A set of scan events from observed beacons within a time span.
```
```swift
```swift
```swift
class ENScanInstance
```
```

The aggregation of attenuations of beacons received during a scan.
```

[

API Reference

Exposure Parameter Limits](/documentation/exposurenotification/exposure-parameter-limits)

The limits for the parameters you use in exposure risk calculations.

### [Summaries](/documentation/ExposureNotification#Summaries)

```swift
```swift
```swift
```swift
class ENExposureDetectionSummary
```
```

A summary of exposures.
```
```swift
```swift
```swift
class ENExposureDaySummary
```
```

The summary of exposure information for a single day.
```
```swift
```swift
```swift
class ENExposureSummaryItem
```
```

The summary of exposures for a specific time period or report type.
```
```

### [Status](/documentation/ExposureNotification#Status)

```swift
```swift
```swift
```swift
enum ENAuthorizationStatus
```
```

A set of cases that indicates the authorization status for the app.
```
```swift
```swift
```swift
enum ENStatus
```
```

A set of cases that represents the overall status of exposure notification on the system.
```
```

### [Errors](/documentation/ExposureNotification#Errors)

```swift
```swift
```swift
```swift
struct ENError
```
```

Errors that the exposure notification framework issues.
```
```swift
```swift
```swift
enum Code
```
```

Error codes that the exposure notification framework issues.
```
```swift
```swift
```swift
let ENErrorDomain: String
```
```

The domain for an error.
```
```swift
```swift
```swift
typealias ENErrorHandler
```
```

The handler for error conditions.
```
```

### [Variables](/documentation/ExposureNotification#Variables)

```swift
```swift
```swift
```swift
var ENRiskWeightDefaultV2: Int
```
```

This weight is not used.
```
```swift
```swift
```swift
var ENRiskWeightMaxV2: Int
```
```

This weight is not used.
```
```swift
```swift
```swift
var EN_FEATURE_GENERAL: Int32
```
```
```
```

### [Type Aliases](/documentation/ExposureNotification#Type-Aliases)

```swift
```swift
```swift
```swift
typealias ENDetectExposuresHandler
```
```

The definition of a handler that returns exposure summaries.
```
```swift
```swift
```swift
typealias ENErrorOutType
```
```

Type for returning NSError’s from functions. Avoids long and repetitious method signatures.
```
```swift
```swift
```swift
typealias ENGetDiagnosisKeysHandler
```
```

The definition of a handler that returns diagnosis keys.
```
```swift
```swift
```swift
typealias ENGetExposureInfoHandler
```
```

The definition of a handler that receives exposure info.
```
```