Framework

# ManagedSettings

Access and change settings with your app while maintaining user privacy and control.

iOS 15.0+iPadOS 15.0+Mac Catalyst 15.0+

## [Overview](/documentation/ManagedSettings#overview)

Managed Settings provides a privacy-preserving way for users to restrict access to certain settings and features on their devices. With the user’s permission, your app can limit media showings, restrict app purchases, lock passcode settings, and configure other device behavior.

![A diagram consisting of three icons with an on-and-off toggle switch below each one. On the left is a Settings icon with an toggle switch representing the on state. In the middle is an App Store icon with a toggle switch represeting the off state. To the right is a Safari icon with a toggle switch representing the on state.](https://docs-assets.developer.apple.com/published/acc1e9abeed55948d8f76d19856eac54/managed-settings-overview%402x.png)

Managed Settings works together with [ManagedSettingsUI](/documentation/ManagedSettingsUI), [DeviceActivity](/documentation/DeviceActivity), and [FamilyControls](/documentation/FamilyControls) to allow your app to restrict, authorize, and monitor device usage. To learn more about authorizing Managed Settings on your app, see [FamilyControls](/documentation/FamilyControls). For more information about monitoring and scheduling device usage with your app, see [DeviceActivity](/documentation/DeviceActivity).

## [Topics](/documentation/ManagedSettings#topics)

### [Essentials](/documentation/ManagedSettings#Essentials)

[

Manage Settings on Devices in a Family Sharing Group](/documentation/managedsettings/connectionwithframeworks)

Empower parents and guardians to configure constraints on other devices while preserving the family’s privacy.

[

Confirming the Effective TV and Movie Ratings](/documentation/managedsettings/readingmedia)

Read the media rating on a device and determine what media to display on your app.

### [Settings](/documentation/ManagedSettings#Settings)

```swift
```swift
```swift
```swift
class ManagedSettingsStore
```
```

A data store that applies settings to the current user or device.
```
```

### [Shield Actions](/documentation/ManagedSettings#Shield-Actions)

```swift
```swift
```swift
```swift
class ShieldActionDelegate
```
```

A class for an extension that handles shield actions.
```
```

### [Family Privacy](/documentation/ManagedSettings#Family-Privacy)

```swift
```swift
```swift
```swift
struct Token
```
```

A representation of an activity, such as an app or website, that doesn’t reveal its identity.
```
```

### [Apps](/documentation/ManagedSettings#Apps)

```swift
```swift
```swift
```swift
struct Application
```
```

A representation of an application on the user’s device.
```
```swift
```swift
```swift
typealias ApplicationToken
```
```

A representation of an application.
```
```

### [Categories](/documentation/ManagedSettings#Categories)

```swift
```swift
```swift
```swift
struct ActivityCategory
```
```

An activity’s category, such as Entertainment or Social.
```
```swift
```swift
```swift
typealias ActivityCategoryToken
```
```

A token that represents a category of app or website activity.
```
```

### [Websites](/documentation/ManagedSettings#Websites)

```swift
```swift
```swift
```swift
struct WebDomain
```
```

An object that represents a website.
```
```swift
```swift
```swift
typealias WebDomainToken
```
```

A representation of a web domain that preserves the user’s privacy.
```
```