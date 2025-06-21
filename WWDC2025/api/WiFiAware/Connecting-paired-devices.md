*   [Wi-Fi Aware](/documentation/wifiaware)
*   Connecting devices for peer-to-peer Wi-Fi

Article

# Connecting devices for peer-to-peer Wi-Fi

Make outgoing and accept incoming secure connections with paired devices.

## [Overview](/documentation/WiFiAware/Connecting-paired-devices#Overview)

With the Wi-Fi Aware™ technology, your app can securely establish peer-to-peer (P2P) connections between Wi-Fi devices. By using the Wi-Fi Aware framework, devices can discover, pair, and communicate with other nearby devices without an internet connection or access point.

For your app to pair devices, or ask the person using your app for access to existing devices, you can use either of the following two methods:

*   [`DeviceDiscoveryUI`](https://developer.apple.com/documentation/devicediscoveryui): Pair any kind of device for device-to-device and app-to-app use cases, such as file transfer and media streaming.
    
*   [`AccessorySetupKit`](https://developer.apple.com/documentation/accessorysetupkit): Pair a person’s personal hardware accessory with the accessory’s companion app, such as for setup and accessory management.
    

After a person pairs a device or grants your app access to a device, the system adds the device to your app’s [`WAPairedDevice.Devices`](/documentation/wifiaware/wapaireddevice/devices) collection, which is accessible through the [`allDevices`](/documentation/wifiaware/wapaireddevice/alldevices) APIs.

### [Connect paired devices](/documentation/WiFiAware/Connecting-paired-devices#Connect-paired-devices)

After your app pairs devices, it can initiate secure peer-to-peer Wi-Fi connections between those devices on demand. The Wi-Fi Aware framework integrates with the [Network](https://developer.apple.com/documentation/Network) framework to provide Wi-Fi Aware connections and related functionality, extending several common networking primitives:

*   [`NetworkBrowser`](/documentation/Network/NetworkBrowser) subscribes to Wi-Fi Aware services on paired devices, and makes outgoing secure connections to them.
    
*   [`NetworkListener`](/documentation/Network/NetworkListener) publishes Wi-Fi Aware services to paired devices, and accepts incoming secure connections from them.
    
*   [`NetworkConnection`](/documentation/Network/NetworkConnection) opens a secure, high-performance data connection to Wi-Fi Aware devices.
    
*   [`NWParameters`](/documentation/Network/NWParameters) configures Wi-Fi Aware parameters.
    
*   [`NWPath`](/documentation/Network/NWPath) fetches Wi-Fi Aware connection statuses and performance metrics.
    
*   [`NWError`](/documentation/Network/NWError) fetches Wi-Fi Aware error statuses.
    

### [Create a listener to publish](/documentation/WiFiAware/Connecting-paired-devices#Create-a-listener-to-publish)

The following code example creates a `NetworkListener` that publishes the `_example-service._tcp` service over Wi-Fi Aware, and accepts incoming connections from the specified paired devices:

```swift

```swift
// Specifies a service.
extension WAPublishableService {
    public static var exampleService: WAPublishableService {
        allServices["_example-service._tcp"]!
    }
}
// Selects devices from the list of the example app's paired devices.
```swift
```swift
let devices = #Predicate<WAPairedDevice> { $0.name?.starts(with: "My Device") ?? false }
```
```
// Constructs a `NetworkListener` to publish the service and accept connections from the selected devices.
// Can optionally provide Wi-Fi Aware configuration parameters in the `datapath:` parameter.
```swift
```swift
let listener = try NetworkListener(for:
```
```
        .wifiAware(.connecting(to: .exampleService, from: .matching(devices), datapath: .defaults)),
    using: {
        TLS()
    })
    .onStateUpdate { listener, state in
    // Processes state updates.
}
```

```

### [Create a browser to subscribe](/documentation/WiFiAware/Connecting-paired-devices#Create-a-browser-to-subscribe)

The following example code creates a `NetworkBrowser` that subscribes for the `_example-service._tcp` service over Wi-Fi Aware, and provides browse results that the system can use to make outgoing connections to the specified paired devices:

```swift

```swift
// Specifies a service.
extension WASubscribableService {
    public static var exampleService: WASubscribableService {
        allServices["_example-service._tcp"]!
    }
}
// Selects `devices` from the list of all paired devices.
```swift
```swift
let devices = #Predicate<WAPairedDevice> { $0.name?.starts(with: "My Device") ?? false }
```
```
// Constructs a `NetworkBrowser` to subscribe for the service on the selected devices. 
```swift
```swift
let browser = NetworkBrowser(
```
```
    for:
        .wifiAware( .connecting(to: .matching(devices),  from: .exampleService))
)
```

```

For additional information on making and managing network connections, refer to the [Network](https://developer.apple.com/documentation/Network) framework.

## [See Also](/documentation/WiFiAware/Connecting-paired-devices#see-also)

### [Essentials](/documentation/WiFiAware/Connecting-paired-devices#Essentials)

[

Building peer-to-peer apps](/documentation/wifiaware/building-peer-to-peer-apps)

Communicate with nearby devices over a secure, high-throughput, low-latency connection by using Wi-Fi Aware.

[

Adopting Wi-Fi Aware](/documentation/wifiaware/adopting-wi-fi-aware)

Add entitlements and declare your app’s services.

[`com.apple.developer.wifi-aware`](/documentation/BundleResources/Entitlements/com.apple.developer.wifi-aware)

The entitlement the system requires for an app to use the Wi-Fi Aware framework.

Beta

[`WiFiAwareServices`](/documentation/BundleResources/Information-Property-List/WiFiAwareServices)

Dictionaries of Wi-Fi Aware services that the app can publish or subscribe to.

Beta