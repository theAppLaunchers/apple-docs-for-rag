

- Network Extension
- NEHotspotConfigurationManager
-  apply(\_:completionHandler:) 

Instance Method

# apply(\_:completionHandler:)

Adds or updates a Wi-Fi network configuration after prompting the user for permission, and then attempts to join the network under certain conditions.

iOS 11.0+iPadOS 11.0+Mac Catalyst 13.1+visionOS 1.0+watchOS 7.0+

``` source
func apply(
    _ configuration: NEHotspotConfiguration,
    completionHandler: (((any Error)?) -> Void)? = nil
)
```

``` source
func apply(_ configuration: NEHotspotConfiguration) async throws
```

## Parameters 

`configuration`  

The configuration to apply to the Wi-Fi network; see NEHotspotConfiguration.

`completionHandler`  

A completion handler called by the method that takes a single argument indicating the outcome of the operation. A value of NEHotspotConfigurationError.userDenied indicates the user refuses to accept the new configuration.

## Discussion

This method attempts to join the network only if it’s found nearby. Also, because of the noticeable delay that the Hotspot 2.0 discovery mechanism may incur, the method doesn’t attempt to join Hotspot 2.0 networks.

In addition to providing an SSID for the Wi-Fi network, your app must provide configuration and authentication information using NEHotspotEAPSettings and NEHotspotHS20Settings. With Hotspot 2.0 networks, the app must provide an HS2.0 domain name instead of an SSID.

This method won’t add a configuration if the same SSID or HS2.0 domain name is already configured through a Mobile Device Management (MDM) profile or a Carrier bundle. If your app configures a hotspot and later an MDM profile or Carrier bundle is installed for a hotspot with the same domain name, the new configuration will overwrite your app’s configuration.

The system calls your completion handler when it has applied the Wi-Fi level configuration. A successful configuration doesnʼt mean the device has joined that Wi-Fi network. To get the current Wi-Fi state, call fetchCurrent(completionHandler:).

Furthermore, joining a Wi-Fi network doesn’t guarantee that the network is fully operational. The system might still be in the process of configuring TCP/IP on that network. If you plan to connect to a service on that network, use an API that waits for connectivity. For example:

- To start a TCP connection to a Bonjour service, use NWConnection.

- To fetch a URL, use URLSession with the waitsForConnectivity option.

## See Also

### Related Documentation

class NEHotspotConfiguration

Configuration settings for a Wi-Fi network.

class NEHotspotEAPSettings

Extensible Authentication Protocol settings for configuring WPA and WPA2 enterprise Wi-Fi networks.

class NEHotspotHS20Settings

Settings for configuring Hotspot 2.0 Wi-Fi networks.

### Creating configurations

class var shared: NEHotspotConfigurationManager

Instantiates NEHotspotConfigurationManager as a singleton, so it can be shared.

