

- Core Bluetooth
- CBMutableCharacteristic
-  value 

Instance Property

# value

The value of the characteristic.

iOS 6.0+iPadOS 6.0+Mac Catalyst 13.1+macOS 10.9+tvOS 9.0+visionOS 1.0+watchOS 2.0+

``` source
var value: Data? { get set }
```

## Discussion

This property contains the value of the characteristic. For example, a temperature measurement characteristic of a health thermometer service may have a value that indicates a temperature in Celsius.

## See Also

### Managing a Mutable Characteristic

var descriptors: [CBDescriptor]?

An array of the characteristic’s descriptors.

var properties: CBCharacteristicProperties

The properties of the characteristic.

var permissions: CBAttributePermissions

The permissions of the characteristic value.

struct CBAttributePermissions

Values that represent the read, write, and encryption permissions for a characteristic’s value.

var subscribedCentrals: [CBCentral]?

A list of centrals that are currently subscribed to the characteristic’s value.

