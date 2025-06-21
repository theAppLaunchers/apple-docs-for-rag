Framework

# FamilyControls

Authorize your app to provide parental controls on a device.

iOS 15.0+iPadOS 15.0+Mac Catalyst 15.0+

## [Overview](/documentation/FamilyControls#Overview)

To authorize your parental controls app, use a shared [`AuthorizationCenter`](/documentation/familycontrols/authorizationcenter) instance. You can authorize parental controls on any device.

![A figure labeled allow activity. It shows an arrow from a Family Sharing logo](https://docs-assets.developer.apple.com/published/e21e1d0eba4c9be965970c6eb2fabd82/family-controls-overview%402x.png)

Important

You must add the Family Controls capability to your app before you call the [`requestAuthorization(for:)`](/documentation/familycontrols/authorizationcenter/requestauthorization\(for:\)) or [`revokeAuthorization(completionHandler:)`](/documentation/familycontrols/authorizationcenter/revokeauthorization\(completionhandler:\)) methods. This capability adds the [`Family Controls`](/documentation/BundleResources/Entitlements/com.apple.developer.family-controls) entitlement to your app. Before submitting your app to the App Store, you must [request permission](https://developer.apple.com/contact/request/family-controls-distribution) to use the entitlement. For more information, see [Adding capabilities to your app](/documentation/Xcode/adding-capabilities-to-your-app).

Authorizing parental controls for a child requires approval from a parent or guardian in the same Family Sharing group. The system displays an authentication sheet on the child’s device, and the parent or guardian approves or denies the authorization request. The system sends the result to your app’s `AuthorizationCenter`.

Authorizing parental controls for an individual requires approval from the owner of the device. The system displays a biometric authentication alert on the individual’s device after the individual approves or denies the authorization request. The system sends the result to your app’s `AuthorizationCenter`.

The Family Controls framework prevents child users, authorized by a parent or guardian, from performing actions that might circumvent the parental controls settings. For example, authorizing an app prevents the child user from deleting the app that provides parental controls. In addition, while a device has at least one app authorized for parental controls by a parent or guardian, the user can’t sign out of iCloud.

In a compatible iPad or iPhone app running in visionOS, authorization attempts always fail.

## [Topics](/documentation/FamilyControls#topics)

### [Authorizations](/documentation/FamilyControls#Authorizations)

```swift
```swift
```swift
```swift
class AuthorizationCenter
```
```

The center for requesting authorization to provide parental controls.
```
```swift
```swift
```swift
enum AuthorizationStatus
```
```

The status of your app’s authorization to provide parental controls.
```

[`Family Controls`](/documentation/BundleResources/Entitlements/com.apple.developer.family-controls)

A Boolean value that indicates whether the app can request or revoke authorization to provide parental controls.
```

### [Account Types](/documentation/FamilyControls#Account-Types)

```swift
```swift
```swift
```swift
enum FamilyControlsMember
```
```

The type of account that Family Controls is currently managing.
```
```

### [User-Selected Apps and Web Domains](/documentation/FamilyControls#User-Selected-Apps-and-Web-Domains)

```swift
```swift
```swift
```swift
struct FamilyActivityPicker
```
```

A view in which users specify applications, web domains, and categories without revealing their choices to the app.
```
```swift
```swift
```swift
struct FamilyActivitySelection
```
```

A collection of applications, categories, and web domains selected by the user.
```
```

### [Activity Labels](/documentation/FamilyControls#Activity-Labels)

[

API Reference

Displaying Activity Labels](/documentation/familycontrols/displayingactivitylabels)

Provide users with a read-only, visual representation of an application, category, or web domain.

### [Errors](/documentation/FamilyControls#Errors)

```swift
```swift
```swift
```swift
enum FamilyControlsError
```
```

Errors the Family Controls framework reports.
```
```