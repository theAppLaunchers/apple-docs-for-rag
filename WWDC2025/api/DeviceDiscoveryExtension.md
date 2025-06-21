Framework

# DeviceDiscoveryExtension

Stream media to a third-party device that a user selects in a system menu.

iOS 16.0+iPadOS 16.0+macOS 15.0+visionOS 1.0+

## [Overview](/documentation/DeviceDiscoveryExtension#overview)

Use DeviceDiscoveryExtension (DDE) to discover third-party media receivers to which your app can stream AV content.

When a user invokes your app’s media-streaming UI, you can offer a third-party, local-network, or Bluetooth device as a streaming destination in a route picker view ([`AVRoutePickerView`](/documentation/AVKit/AVRoutePickerView)). The figure below illustrates actors in the discovery process. As depicted in the System section, your app’s device discovery extension loads when the view displays.

![A flowchart with four boxes in a horizontal row from left to right, each labeled respectively: user, app, system, and third-party device. Lines that represent channels extend downward from each box. At the top of the user channel is the start of a continuous arrow that traces a path with switchbacks through all the channels. Multiple steps of the device discovery process are shown in this path with arrows that indicate the order in which they occur, from the user invoking it until the third-party device plays the media.](https://docs-assets.developer.apple.com/published/1729cdc9d04d8250ae66a99bd7c12dfa/media-4056835%402x.png)

Once the extension loads:

*   The extension runs in a system process and searches the local network and Bluetooth devices for a specific media receiver.
    
*   When the extension finds the device, it returns the device to the system, which displays it in the picker view as an available option.
    
*   The user makes a selection and the system passes the chosen device to the app, which can then stream media to the device.
    

Because DDE runs in a system sandbox, the extension doesn’t need to ask the user for local-network or Bluetooth permissions. The picker view displays discovered third-party devices and protocols in the same system menu as AirPlay, which provides a unified device-selection experience.

Note

To stream to a third-party device that you don’t manufacture, bundle your app with the device discovery extension that the manufacturer provides as part of its SDK.

## [Topics](/documentation/DeviceDiscoveryExtension#topics)

### [Essentials](/documentation/DeviceDiscoveryExtension#Essentials)

[

Discovering a third-party media-streaming device](/documentation/devicediscoveryextension/discovering-a-third-party-media-streaming-device)

Build an extension that streams media to a server app in iOS or macOS.

[`Media Device Discovery Extension`](/documentation/BundleResources/Entitlements/com.apple.developer.media-device-discovery-extension)

An entitlement for an app extension that adds a specific third-party media receiver to a system device-picker UI.

### [Extension](/documentation/DeviceDiscoveryExtension#Extension)

```swift
```swift
```swift
```swift
protocol DDDiscoveryExtension
```
```

A specification that enables the framework to start and stop the extension’s discovery process.
```
```swift
```swift
```swift
class DDDiscoverySession
```
```

An object that relays device discovery events from the extension to the system.
```
```swift
```swift
```swift
class DDDiscoveryExtensionConfiguration
```
```

An object that manages the extension’s communication with the framework.
```
```swift
```swift
```swift
protocol DDDiscoveryExtensionConfigurationProtocol
```
```

A specification that provides a communication channel between the extension and the framework.
```
```

### [Life cycle](/documentation/DeviceDiscoveryExtension#Life-cycle)

```swift
```swift
```swift
```swift
class DDDeviceEvent
```
```

An object that provides a device or communicates its change in status.
```
```swift
```swift
```swift
enum EventType
```
```

Identifiers for the types of events that occur in the device discovery life cycle.
```
```swift
```swift
```swift
func DDEventTypeToString(DDDeviceEvent.EventType) -> String
```
```

Returns human-readable text for the specified event identifier.
```
```swift
```swift
```swift
typealias DDEventHandler
```
```

A function that the extension invokes to signal an event.
```
```

### [Device information](/documentation/DeviceDiscoveryExtension#Device-information)

```swift
```swift
```swift
```swift
class DDDevice
```
```

An object that describes a discovered device of interest.
```
```swift
```swift
```swift
enum Category
```
```

An option that determines the icon for the device in the picker UI.
```
```swift
```swift
```swift
enum DDDeviceState
```
```

A state that represents the level of user interaction with the device.
```
```swift
```swift
```swift
func DDDeviceCategoryToString(DDDevice.Category) -> String
```
```

Returns human-readable text for the specified identifier that describes a device’s category.
```
```swift
```swift
```swift
func DDDeviceStateToString(DDDeviceState) -> String
```
```

Returns human-readable text for the specified identifier that describes a device’s status.
```
```swift
```swift
```swift
enum Protocol
```
```

An identifier for the manner in which an app interacts with a device.
```
```swift
```swift
```swift
func DDDeviceProtocolToString(DDDevice.Protocol) -> String
```
```

Returns human-readable text for the specified protocol identifier.
```
```swift
```swift
```swift
struct DDDeviceProtocolString
```
```

String values for the manner in which an app interacts with a device.
```
```swift
```swift
```swift
func DDDeviceMediaPlaybackStateToString(DDDevice.MediaPlaybackState) -> String
```
```

Returns human-readable text for the specified media playback state.
```
```

### [Errors](/documentation/DeviceDiscoveryExtension#Errors)

```swift
```swift
```swift
```swift
struct DDError
```
```

An error that the framework reports.
```
```swift
```swift
```swift
enum Code
```
```

Codes that identify errors that can occur during the framework’s use.
```
```swift
```swift
```swift
typealias DDErrorHandler
```
```

A function that executes code you provide when an operation returns an error or completes successfully.
```
```swift
```swift
```swift
typealias DDErrorOutType
```
```

A type for framework functions that return error references.
```
```swift
```swift
```swift
let DDErrorDomain: String
```
```

A unique error domain for the framework.
```
```

### [Reference](/documentation/DeviceDiscoveryExtension#Reference)

[

API Reference

DeviceDiscoveryExtension Enumerations](/documentation/devicediscoveryextension/devicediscoveryextension-enumerations)