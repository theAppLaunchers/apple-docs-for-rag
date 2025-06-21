Framework

# Nearby Interaction

Locate and interact with nearby devices using identifiers, distance, and direction.

iOS 14.0+iPadOS 14.0+Mac Catalyst 14.0+macOS 11.0+watchOS 8.0+

## [Overview](/documentation/NearbyInteraction#overview)

Use Nearby Interaction in your app to acquire the position of devices with an Ultra Wideband (UWB) chip, such as iPhone 11 or later, Apple Watch, and third-party accessories. To participate in an interaction, devices in physical proximity run an app and share their position and device tokens that uniquely identify them. When the app runs in the foreground, Nearby Interaction notifies the interaction session of the peer’s location by reporting the peer’s direction and distance in meters.

Apple devices use the high-frequency capabilities of the UWB chip to share their positions in the physical environment and enable fluid, interactive sessions. For example:

*   A multiuser AR experience that places virtual water balloons in the hands of its participants
    
*   A taxi or rideshare app that employs a peer user’s direction in real time to identify the relative locations of a driver and a customer
    
*   A game app that enables a user to control a paddle with their device and respond to a moving ball on the peer user’s screen, as in the following figure
    

![An illustration of two hands, each holding an iPhone. Arrows extend from the phones to indicate the users’ physical movement. Onscreen, the app displays a ball and paddle game where the first user’s movement slides the bottom paddle left or right, and the opponent’s movement slides the top paddle left or right. In the center of the screen, a ball with motion lines indicates the movement of the ball as it bounces off the first user’s paddle and heads to the upper-right corner of the screen, which isn’t guarded by the opponent’s paddle. ](https://docs-assets.developer.apple.com/published/ebda45d0d49a7c9ff21289ec31ef90e2/media-3880159%402x.png)

For guidance on designing nearby interactions, see the [Human Interface Guidelines > Nearby interactions](https://developer.apple.com/design/human-interface-guidelines/nearby-interactions).

### [Interact with Apple Watch](/documentation/NearbyInteraction#Interact-with-Apple-Watch)

The UWB chip-capable Apple Watch running watchOS 8 supports Nearby Interaction sessions. Apps share discovery tokens to begin an interaction session in watchOS using a custom server, [Core Bluetooth](/documentation/CoreBluetooth), LAN (TCP/UDP), or [Watch Connectivity](/documentation/WatchConnectivity).

Nearby Interaction in iOS provides a peer device’s distance and direction, whereas Nearby Interaction in watchOS provides only a peer device’s distance.

### [Interact with third-party devices](/documentation/NearbyInteraction#Interact-with-third-party-devices)

In iOS 15 and later and watchOS 8 and later, U1-enabled devices can interact with third-party accessories you partner with or develop using the [Ultra Wideband (UWB) third-party device specification](https://developer.apple.com/nearby-interaction/specification). To begin an interaction session with a third-party accessory, establish a data link with the accessory, receive its configuration data, and create an [`NINearbyAccessoryConfiguration`](/documentation/nearbyinteraction/ninearbyaccessoryconfiguration). The framework provides configuration data for your device through [`session(_:didGenerateShareableConfigurationData:for:)`](/documentation/nearbyinteraction/nisessiondelegate/session\(_:didgenerateshareableconfigurationdata:for:\)) that your app sends to the accessory to begin detecting the accessory’s range. For more information on accessory interaction, see [`NINearbyAccessoryConfiguration`](/documentation/nearbyinteraction/ninearbyaccessoryconfiguration).

Note

The [`supportsPreciseDistanceMeasurement`](/documentation/nearbyinteraction/nidevicecapability/supportsprecisedistancemeasurement) function returns [`false`](/documentation/swift/false) in Mac apps built with Mac Catalyst. For a compatible iPad or iPhone app running in visionOS, framework features are unavailable, and any calls you make to the framework APIs have no effect.

### [Using Nearby Interaction in the background](/documentation/NearbyInteraction#Using-Nearby-Interaction-in-the-background)

While your app is in the foreground, it can freely use Nearby Interaction to perform ranging between UWB devices. When the app moves to the background, it can perform UWB ranging only with devices that are Bluetooth Low Energy (LE)-paired and connected.

In iOS 18.4 and later, your app can continue ranging in the background with any supported device if the app starts a Live Activity as it goes to the background. For more information about creating Live Activities, see [ActivityKit](/documentation/ActivityKit).

Note

Both these forms of background activity require that you enable the appropriate capability in Xcode. In your target’s Signing & Capabilities tab, add the “Background Modes” capability, then select “Uses Nearby Interaction”.

## [Topics](/documentation/NearbyInteraction#topics)

### [Setup](/documentation/NearbyInteraction#Setup)

[

Initiating and maintaining a session](/documentation/nearbyinteraction/initiating-and-maintaining-a-session)

Measure the relative position of a nearby device and coach the user to sustain interaction.

```swift
```swift
```swift
class NISession
```
```

An object that identifies a unique connection between two peer devices.
```

### [Authorization](/documentation/NearbyInteraction#Authorization)

[`NSNearbyInteractionUsageDescription`](/documentation/BundleResources/Information-Property-List/NSNearbyInteractionUsageDescription)

A request for user permission to begin an interaction session with nearby devices.

### [Phone interaction](/documentation/NearbyInteraction#Phone-interaction)

[

Implementing Interactions Between Users in Close Proximity](/documentation/nearbyinteraction/implementing-interactions-between-users-in-close-proximity)

Enable devices to access relative positioning information.

[

Discovering peers with Multipeer Connectivity](/documentation/nearbyinteraction/discovering-peers-with-multipeer-connectivity)

Exchange discovery tokens over the local network.

[

Extending advanced direction finding and ranging](/documentation/nearbyinteraction/extending-advanced-direction-finding-and-ranging)

Extend your app’s direction finding capabilities with data from Ultra Wideband devices.

```swift
```swift
```swift
class NINearbyPeerConfiguration
```
```

A configuration that enables interaction between iPhone or Apple Watch devices.
```

### [Watch interaction](/documentation/NearbyInteraction#Watch-interaction)

[

Implementing proximity-based interactions between a phone and watch](/documentation/nearbyinteraction/implementing-proximity-based-interactions-between-a-phone-and-watch)

Interact with a nearby Apple Watch by measuring its distance to a paired iPhone.

### [Third-party accessories](/documentation/NearbyInteraction#Third-party-accessories)

[

Implementing spatial interactions with third-party accessories](/documentation/nearbyinteraction/implementing-spatial-interactions-with-third-party-accessories)

Establish a connection with a nearby accessory to receive periodic measurements of its distance from the user.

```swift
```swift
```swift
class NINearbyAccessoryConfiguration
```
```

A configuration that enables interaction between iPhone and third-party accessories.
```

### [Periodic updates](/documentation/NearbyInteraction#Periodic-updates)

```swift
```swift
```swift
```swift
class NINearbyObject
```
```

Location information for a peer device in an interaction session.
```
```swift
```swift
```swift
protocol NISessionDelegate
```
```

An object that monitors and reacts to session updates.
```
```

### [Camera assistance](/documentation/NearbyInteraction#Camera-assistance)

[

Finding devices with precision](/documentation/nearbyinteraction/finding-devices-with-precision)

Leverage the spatial awareness of ARKit and Apple Ultra Wideband Chips in your app to guide users to a nearby device.

```swift
```swift
```swift
class NIAlgorithmConvergence
```
```

An object that provides the state and reason for user coaching recommendations.
```
```swift
```swift
```swift
enum NIAlgorithmConvergenceStatus
```
```

The possible states of Camera Assistance.
```

[

API Reference

Algorithm Convergence Status](/documentation/nearbyinteraction/algorithm-convergence-status)

The possible Objective-C states of Camera Assistance.

### [Errors](/documentation/NearbyInteraction#Errors)

```swift
```swift
```swift
```swift
struct NIError
```
```

An error Nearby Interaction reports.
```
```swift
```swift
```swift
enum Code
```
```

Codes that identify errors in Nearby Interaction.
```
```swift
```swift
```swift
let NIErrorDomain: String
```
```

A unique error domain for Nearby Interaction.
```
```

### [Deprecated](/documentation/NearbyInteraction#Deprecated)

Avoid using deprecated configuration in your apps.

[`NSNearbyInteractionAllowOnceUsageDescription`](/documentation/BundleResources/Information-Property-List/NSNearbyInteractionAllowOnceUsageDescription)

A one-time request for user permission to begin an interaction session with nearby devices.

Deprecated

### [Classes](/documentation/NearbyInteraction#Classes)

```swift
```swift
```swift
```swift
class NIDLTDOAConfiguration
```
```

A session configuration that enables UWB Down Link Time Difference of Arrival(DL-TDoA) ranging with nearby anchors.

Beta
```
```swift
```swift
```swift
class NIDLTDOAMeasurement
```
```

Represents a single measurement relative to a DL-TDOA anchor.

Beta
```
```

### [Enumerations](/documentation/NearbyInteraction#Enumerations)

```swift
```swift
```swift
```swift
enum NIDLTDOACoordinatesType
```
```

The coordinate types of DL-TDOA measurement updates that Nearby Interaction supports.

Beta
```
```swift
```swift
```swift
enum NIDLTDOAMeasurementType
```
```

The measurement types of DL-TDOA measurement updates that Nearby Interaction supports.

Beta
```
```