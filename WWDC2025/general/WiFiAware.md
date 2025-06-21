Framework

# Wi-Fi Aware

Securely pair and connect to external devices over peer-to-peer Wi-Fi.

iOS 26.0+BetaiPadOS 26.0+Beta

## [Overview](/documentation/WiFiAware#Overview)

The Wi-Fi Aware™ technology (also known as Neighbor Awareness Networking or NAN) is a Wi-Fi Alliance™ standard specification that enables devices to securely discover, pair, and communicate with nearby devices without an internet connection or access point. Your app can use the Wi-Fi Aware framework to connect with Wi-Fi Aware certified accessories. The framework offers a secure and standardized way to establish peer-to-peer (P2P) connections between Wi-Fi devices, providing networking capabilities such as:

*   High-bandwidth and low-latency data transfers
    
*   Connections to paired devices that are authenticated and encrypted at the Wi-Fi layer
    
*   Simultaneous connections to multiple Wi-Fi Aware devices
    
*   Simultaneous use of Wi-Fi Aware devices and a Wi-Fi infrastructure network
    
*   Fully peer-to-peer topology, allowing peers to come and go without breaking connections to other peers
    

The Wi-Fi Aware technology works without the need for Wi-Fi infrastructure networks, cellular links, internet connections, or cloud servers. Your app can pair Wi-Fi Aware devices using [AccessorySetupKit](https://developer.apple.com/documentation/accessorysetupkit/) or [DeviceDiscoveryUI](https://developer.apple.com/documentation/devicediscoveryui). When paired, your app can create secure, authenticated, and encrypted peer-to-peer connections between paired devices on-demand, using the Wi-Fi Aware and [Network](https://developer.apple.com/documentation/Network) frameworks.

Important

The following Apple devices support the Wi-Fi Aware framework:

*   iPhone 12 and later
    
*   iPad (10th generation) and later
    
*   iPad Air (4th generation) and later
    
*   iPad Pro 11-inch (3rd generation) and later
    
*   iPad Pro 12.9-inch (5th generation) and later
    
*   iPad mini (6th generation) and later
    

## [Topics](/documentation/WiFiAware#topics)

### [Essentials](/documentation/WiFiAware#Essentials)

[

Building peer-to-peer apps](/documentation/wifiaware/building-peer-to-peer-apps)

Communicate with nearby devices over a secure, high-throughput, low-latency connection by using Wi-Fi Aware.

[

Connecting devices for peer-to-peer Wi-Fi](/documentation/wifiaware/connecting-paired-devices)

Make outgoing and accept incoming secure connections with paired devices.

[

Adopting Wi-Fi Aware](/documentation/wifiaware/adopting-wi-fi-aware)

Add entitlements and declare your app’s services.

[`com.apple.developer.wifi-aware`](/documentation/BundleResources/Entitlements/com.apple.developer.wifi-aware)

The entitlement the system requires for an app to use the Wi-Fi Aware framework.

[`WiFiAwareServices`](/documentation/BundleResources/Information-Property-List/WiFiAwareServices)

Dictionaries of Wi-Fi Aware services that the app can publish or subscribe to.

### [Host capabilities](/documentation/WiFiAware#Host-capabilities)

```swift
```swift
```swift
```swift
struct WACapabilities
```
```

A structure that checks the host device’s supported features and capabilities.
```
```swift
```swift
```swift
enum Feature
```
```

Features that your app’s current host device can support.
```
```

### [Services to discover](/documentation/WiFiAware#Services-to-discover)

```swift
```swift
```swift
```swift
protocol WAService
```
```

A protocol that defines a service that a device can publish or subscribe to.
```
```swift
```swift
```swift
struct WASubscribableService
```
```

A service your app discovers on remote devices and can connect to.
```
```swift
```swift
```swift
struct WAPublishableService
```
```

A service, hosted by your app, that remote devices can connect to.
```
```

### [Paired devices](/documentation/WiFiAware#Paired-devices)

```swift
```swift
```swift
```swift
struct WAPairedDevice
```
```

A known Wi-Fi Aware device that your app can connect to.
```
```swift
```swift
```swift
typealias Devices
```
```

A dictionary holding a snapshot of currently paired devices accessible and known to your app.
```
```swift
```swift
```swift
struct DevicesSequence
```
```

A sequence that vends updates to a paired device list, as the list changes.
```
```swift
```swift
```swift
struct PairingInfo
```
```

A collection of unauthenticated information the system receives from a device before it’s paired for the first time.
```
```

### [Subscriber](/documentation/WiFiAware#Subscriber)

```swift
```swift
```swift
```swift
struct WASubscriberBrowser
```
```

The structure that configures a network browser to subscribe to a Wi-Fi Aware service and make outgoing connections to paired devices.
```
```swift
```swift
```swift
struct Action
```
```

The structure that configures the Wi-Fi Aware subscriber operation the network browser performs.
```
```swift
```swift
```swift
struct Devices
```
```

The structure that determines the devices to connect to.
```
```

### [Publisher](/documentation/WiFiAware#Publisher)

```swift
```swift
```swift
```swift
struct WAPublisherListener
```
```

Configures a network listener to publish a service over Wi-Fi Aware and accept incoming connections from paired devices.
```
```swift
```swift
```swift
struct Action
```
```

The structure that configures the Wi-Fi Aware publisher operation that the network listener performs.
```
```swift
```swift
```swift
struct Devices
```
```

The structure that determines the devices to connect to.
```
```swift
```swift
```swift
struct DatapathParameters
```
```

The parameter that sets the initial Wi-Fi Aware data path configuration for any devices that are connected.
```
```

### [Parameters](/documentation/WiFiAware#Parameters)

[`final class NWParameters`](/documentation/Network/NWParameters)

An object that stores the protocols to use for connections, options for sending data, and network path constraints.

```swift
```swift
```swift
struct NWParametersBuilder<Top, each P> where Top : NetworkProtocolOptions, repeat each P : NetworkProtocolOptions
```
```
```
```swift
```swift
```swift
struct WAParameters
```
```

Parameters configuring a Wi-Fi Aware data path connection.
```

### [Connections](/documentation/WiFiAware#Connections)

```swift
```swift
```swift
```swift
struct WAEndpoint
```
```

The endpoint of a Wi-Fi Aware connection.
```
```

### [Connection performance](/documentation/WiFiAware#Connection-performance)

```swift
```swift
```swift
```swift
struct NWPath
```
```

An object that contains information about the properties of the network that a connection uses, or that are available to your app.
```
```swift
```swift
```swift
struct WAPath
```
```

A representation of the current Wi-Fi Aware path.
```
```swift
```swift
```swift
enum WAPerformanceMode
```
```

The performance mode that indicates what performance criterion to prioritize.
```
```swift
```swift
```swift
enum WAAccessCategory
```
```

The underling quality-of-service (QoS) the Wi-Fi layer uses to transmit data packets from a connection over the air.
```
```swift
```swift
```swift
struct WAPerformanceReport
```
```

The current performance state of the data path.
```
```

### [Errors](/documentation/WiFiAware#Errors)

```swift
```swift
```swift
```swift
enum NWError
```
```

The errors returned by objects in the Network framework.
```
```swift
```swift
```swift
enum WAError
```
```

An error in Wi-Fi Aware.
```
```

Beta Software

This documentation contains preliminary information about an API or technology in development. This information is subject to change, and software implemented according to this documentation should be tested with final operating system software.

[Learn more about using Apple's beta software](https://developer.apple.com/support/beta-software/)