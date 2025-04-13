

- Network Extension
- NEHotspotConfiguration
-  joinOnce 

Instance Property

# joinOnce

Restricts the lifetime of a configuration to the operating status of the app that created it.

iOS 11.0+iPadOS 11.0+Mac Catalyst 13.1+visionOS 1.0+watchOS 7.0+

``` source
var joinOnce: Bool { get set }
```

## Discussion

Optional. When `joinOnce` is set to `true,` the hotspot remains configured and connected only as long as the app that configured it is running in the foreground. The hotspot is disconnected and its configuration is removed when any of the following events occurs:

- The app stays in the background for more than 15 seconds.

- The device sleeps.

- The app crashes, quits, or is uninstalled.

- The app connects the device to a different Wi-Fi network.

- The user connects the device to a different Wi-Fi network.

To disconnect the device from a hotspot configured with `joinOnce` set to `true`, call removeConfiguration(forSSID:).

## See Also

### Accessing configuration properties

var ssid: String

The SSID of an open, WEP, WPA/WPA2 personal, or WPA/WPA2 enterprise Wi-Fi network.

var ssidPrefix: String

The string used to match networks against a known SSID prefix.

var lifeTimeInDays: NSNumber

The number of days the network retains the associated configuration.

var hidden: Bool

A Boolean value that indicates the visibility of the SSID.

