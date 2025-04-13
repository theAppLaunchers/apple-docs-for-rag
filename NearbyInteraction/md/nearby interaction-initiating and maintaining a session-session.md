

- Nearby Interaction
-  Initiating and maintaining a session 

Article

# Initiating and maintaining a session

Measure the relative position of a nearby device and coach the user to sustain interaction.

## Overview

When an app reacts to the relative position of another device, it creates a unique experience based on the user’s environment. For example, after the user requests a lift in a ride share app, the app can display a graphic that points in the direction of the driver as they approach.

To create these kinds of spatial interactions with nearby people or objects, your app discovers the available peers with a network technology you choose. If the peer app responds positively, the apps agree to commence receiving respective positions.

To perform this discovery and handshake, the app implements custom code using a network technology you choose. Common examples are Core Bluetooth, Multipeer Connectivity, Watch Connectivity, or a custom server deployment. Over the network, the apps share specific data that the system requires to begin an interaction session, such as the session’s discoveryToken.

The NIConfiguration subclass that you choose decides the device type for an interaction: an Apple device or third-party accessory. When you pass the configuration to an NISession instance and run it, the framework provides your app with the position of the nearby object periodically through NISessionDelegate callbacks.

Your session’s delegate also monitors critical state by implementing callbacks. For example, to keep an interaction going, you may need to guide the user to conform to range and line of sight requirements of the Ultra Wideband (UWB) chips.

### Define a usage description

Before the system allows an interaction session to start, the framework checks for user permission to share the device’s position with a nearby peer. The first time the app runs, the framework presents a prompt that displays the textual value of NSNearbyInteractionUsageDescription in the app’s `Info.plist`. This property describes the benefits of position sharing in an interaction session.

The system persists the user’s choice in Settings. After your app runs for the first time, it consults the user preference in Settings before it begins a new interaction session.

Alternatively, the user adjusts Nearby Interaction permission in Privacy Settings.

### Confirm device and feature support

Apple devices with a UWB chip support Nearby Interaction. To check whether the user’s device supports Nearby Interaction and the specific features your app requires, inspect deviceCapabilities.

```
if NISession.deviceCapabilities.supportsDirectionMeasurement {
    // Interact using device distance and direction.
} else if NISession.deviceCapabilities.supportsPreciseDistanceMeasurement {
    // Interact using distance only.
} 
```

On iOS 15 and earlier, check the session’s isSupported flag.

```
var isSupported : Bool
if #available(iOS 16.0, watchOS 9.0, *) {
    isSupported = NISession.deviceCapabilities.supportsPreciseDistanceMeasurement
} else {
    isSupported = NISession.isSupported
}
if isSupported {
    // Initiate an interaction session.
}
```

In addition to iPhone, Nearby Interaction supports Apple Watch and third-party accessories in iOS 15 and later. If your app runs on iOS 14, check the iOS version of the user’s device before trying to interact with devices other than iPhone.

```
if #available(iOS 15, *) {
    // Pursue interaction with nearby third-party accessories or Apple Watch.
} else {
    // Interact only with iPhone.
}
```

### Locate peers and exchange discovery data

Your app checks for nearby peers using a network technology that you choose.

- To locate peers over the local network, see Discovering peers with Multipeer Connectivity.

- To locate a paired Apple Watch using Watch Connectivity, see Implementing proximity-based interactions between a phone and watch.

- To locate a third-party accessory using Core Bluetooth, see Implementing spatial interactions with third-party accessories.

Note

Alternatively, apps can discover each other over the internet through a custom server deployment you may set up. Since Nearby Interaction works within a limited local range, the deployment can match peers by using GPS coordinates.

Apps then exchange data in a particular format that depends on the device types in the interaction session. For interaction between Apple devices, peers share their discovery tokens (discoveryToken). For interactions with a third-party accessory, the accessory sends your app a configuration data object as outlined in the UWB third-party device specification.

### Create a configuration object

The app creates a configuration object with the information it receives from the peer. The type of information depends on the particular peer. From an iPhone or Apple Watch, the app receives a discovery token and passes it to the init(peerToken:) initializer of NINearbyPeerConfiguration.

```
let configuration = NINearbyPeerConfiguration(peerToken: peerDiscoverToken)
```

From a peer accessory, the app receives a configuration data object and passes it into the init(data:) initializer of NINearbyAccessoryConfiguration.

```
configuration = try NINearbyAccessoryConfiguration(data: configData)
```

Tip

To enable interaction in the background for Bluetooth accessories on iOS 16, call the init(accessoryData:bluetoothPeerIdentifier:) initializer instead and pass in the accessory’s Bluetooth identifier.

### Respond to session delegate callbacks

To receive peer positions and react to events in the Nearby Interaction life cycle, the app implements a delegate that conforms to NISessionDelegate.

When the framework detects the location of a nearby peer, it provides the peer’s current position to the delegate’s session(_:didUpdate:) implementation. When interacting with a supported third-party accessory, the framework calls session(_:didGenerateShareableConfigurationData:for:), passing in configuration data that the app sends to the accessory.

The following describes errors that invalidate a session. The framework passes the error into the session(_:didInvalidateWith:) callback.

- The delegate receives NIError.Code.invalidConfiguration if the NINearbyPeerConfiguration discovery token is invalid.

- The delegate receives NIError.Code.invalidConfiguration if an accessory configuration lacks an accessoryDiscoveryToken.

- The delegate receives NIError.Code.userDidNotAllow if the user declines the access prompt.

If a user backgrounds the app, Nearby Interaction suspends the session and notifies the delegate through sessionWasSuspended(_:).

If a peer device closes the app or moves out of range of the UWB chip, Nearby Interaction times out the peer. The delegate receives the reason the peer left through the session(_:didRemove:reason:) callback.

### Coach the user on range, orientation, and line of sight

Nearby Interaction works best when peer iPhone devices are:

- Within 9 meters of each other

- In portrait orientation

- Facing each other with their back camera

An iPhone detects a peer device’s direction when it appears within the narrow line of sight illustrated by the conic region in the following diagram.

The arrow in the center of the cone represents the direction vector, which extends outward from the center of the back of the device in the direction of the peer. The arrow can point anywhere within the cone in the direction of the peer. However, the line of sight must be clear of obstacles that could interfere with the UWB chip’s communication, such as people, vehicles, or walls.

The app can present instructional text to facilitate interactions. For example, if a peer device is out of range, the delegate reads distance and direction as `nil`. If a peer device is out of the line of sight, the delegate reads the direction as `nil`.

In Objective-C, if a peer device is out of range, the delegate reads distance as NINearbyObjectDistanceNotAvailable, and direction as NINearbyObjectDirectionNotAvailable. If a peer device is out of the line of sight, the delegate reads the direction as NINearbyObjectDirectionNotAvailable.

In either situation, the app could request that the user approach the peer to resume the interaction.

Note

Because it provides no direction vector, Apple Watch doesn’t conform to line of sight guidelines.

### Increase line of sight with Camera Assistance

In iOS 16, Camera Assistance (isCameraAssistanceEnabled) increases the device’s line of sight to a larger area that surrounds the device. This provides a nearby object’s distance and direction in a wider range of environmental conditions, in addition to the object’s horizontalAngle and verticalDirectionEstimate.

Note

Camera Assistance provides a direction outside of the narrow line of sight only after first encountering the peer device once within the narrow line of sight.

To use Camera Assistance in an interaction session, ensure the device supports the feature first by checking the value of supportsCameraAssistance.

## See Also

### Setup

class NISession

An object that identifies a unique connection between two peer devices.

