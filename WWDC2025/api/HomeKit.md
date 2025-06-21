Framework

# HomeKit

Configure, control, and communicate with home automation accessories.

iOS 8.0+iPadOS 8.0+Mac Catalyst 14.0+tvOS 10.0+visionOS 1.0+watchOS 2.0+

## [Overview](/documentation/HomeKit#overview)

HomeKit enables your app to coordinate and control home automation accessories from multiple vendors to present a coherent, user-focused interface.

![The diagram depicts a stylized phone emitting waves to indicate communication with a house pictured as a central icon. Four icons are arranged in a semi-circle to the right of the house icon, depicting connected accessories including a garage door, a thermometer, a sliding light switch, and a lamp.](https://docs-assets.developer.apple.com/published/d33b070d6684f4f8ae1ed27b980f946b/media-3111422%402x.png)

Using HomeKit, your app can:

*   Discover HomeKit-compatible automation accessories and add them to a persistent, cross-device home configuration database.
    
*   Display, edit, and act upon the data in the home configuration database.
    
*   Communicate with configured accessories and services in order to perform actions like turning on the lights in the living room.
    

## [Topics](/documentation/HomeKit#topics)

### [Essentials](/documentation/HomeKit#Essentials)

[

Enabling HomeKit in your app](/documentation/homekit/enabling-homekit-in-your-app)

Declare your app’s intention to use HomeKit, and get permission from the user to access home automation accessories.

[`HomeKit Entitlement`](/documentation/BundleResources/Entitlements/com.apple.developer.homekit)

A Boolean value that indicates whether users of the app may manage HomeKit-compatible accessories.

[`NSHomeKitUsageDescription`](/documentation/BundleResources/Information-Property-List/NSHomeKitUsageDescription)

A message that tells the user why the app is requesting access to the user’s HomeKit configuration data.

### [Home Manager](/documentation/HomeKit#Home-Manager)

[

Configuring a home automation device](/documentation/homekit/configuring-a-home-automation-device)

Give users a familiar experience when they manage HomeKit accessories.

[

Testing your app with the HomeKit Accessory Simulator](/documentation/homekit/testing-your-app-with-the-homekit-accessory-simulator)

Install the HomeKit Accessory Simulator to help you debug your HomeKit-enabled app.

```swift
```swift
```swift
class HMHomeManager
```
```

The manager for a collection of one or more of a user’s homes.
```

### [Accessories](/documentation/HomeKit#Accessories)

```swift
```swift
```swift
```swift
class HMAccessorySetupManager
```
```

An object that setups up new accessories.
```
```swift
```swift
```swift
class HMAccessorySetupResult
```
```

A result object describing information about a successful accessory setup request.
```
```swift
```swift
```swift
class HMAccessorySetupRequest
```
```

An object that describes how to add and setup up new accessories.
```

[

Interacting with a home automation network](/documentation/homekit/interacting-with-a-home-automation-network)

Find all the automation accessories in the primary home and control their state.

```swift
```swift
```swift
class HMAccessory
```
```

A home automation accessory, like a garage door opener or a thermostat.
```
```swift
```swift
```swift
class HMService
```
```

A controllable feature of an accessory, like a light attached to a garage door opener.
```
```swift
```swift
```swift
class HMCharacteristic
```
```

A specific characteristic of a service, like the brightness of a dimmable light or its color temperature.
```
```swift
```swift
```swift
class HMMediaSourceDisplayOrderProfile
```
```

An interface from which to read and, if allowed by the accessory, update the ordering of input sources.
```
```

### [Action Sets](/documentation/HomeKit#Action-Sets)

```swift
```swift
```swift
```swift
class HMActionSet
```
```

A collection of actions that you trigger as a group.
```
```swift
```swift
```swift
class HMTimerTrigger
```
```

A trigger to activate an action set based on a periodic timer.
```
```swift
```swift
```swift
class HMEventTrigger
```
```

A trigger to activate an action set based on a set of events and optional conditions.
```
```

### [Errors](/documentation/HomeKit#Errors)

```swift
```swift
```swift
```swift
struct HMError
```
```

An error HomeKit returns.
```
```swift
```swift
```swift
let HMErrorDomain: String
```
```

A string that identifies the HomeKit error domain.
```
```swift
```swift
```swift
enum Code
```
```

Possible error values that can be returned from HomeKit APIs.
```
```swift
```swift
```swift
typealias HMErrorBlock
```
```

A completion block that provides an error.
```
```

### [Classes](/documentation/HomeKit#Classes)

```swift
```swift
```swift
```swift
class HMAccessorySetupPayload
```
```

A payload for authenticating a HomeKit accessory.
```
```