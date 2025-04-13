

- External Accessory
- EAWiFiUnconfiguredAccessory
-  model 

Instance Property

# model

The model name of accessory.

iOS 8.0+iPadOS 8.0+Mac Catalyst 13.1+tvOS 10.0+visionOS 1.0+

``` source
var model: String { get }
```

## See Also

### Getting Information About the Accessory

var name: String

The name of the accessory.

var manufacturer: String

The name of the accessory’s manufacturer.

var ssid: String

The Wi-Fi SSID of the accessory.

var macAddress: String

The primary MAC address of the accessory.

var properties: EAWiFiUnconfiguredAccessoryProperties

The properties the accessory supports.

struct EAWiFiUnconfiguredAccessoryProperties

Options that can be combined using the C bitwise `OR` operator to represent the properties of an unconfigured accessory.

