

- HomeKit
-  HMCharacteristicTypeIdentify 

Global Variable

# HMCharacteristicTypeIdentify

A control you can use to ask the accessory to identify itself.

iOS 8.0+iPadOS 8.0+Mac Catalyst 8.0+tvOS 10.0+visionOS 1.0+watchOS 2.0+

``` source
let HMCharacteristicTypeIdentify: String
```

## Discussion

Use the corresponding write-only Boolean value to ask the accessory to identify itself in the physical world. The identification mechanism, if supported, is specific to the accessory. For example, a light bulb might change state briefly, flashing on or off, to indicate that it has received this command.

## See Also

### Accessory identification

let HMCharacteristicTypeName: String

The name of the accessory.

let HMCharacteristicTypeVersion: String

The version of the accessory.

let HMCharacteristicTypeLogs: String

Log data for the accessory.

let HMCharacteristicTypeAdminOnlyAccess: String

An indicator of whether the accessory accepts only administrator access.

let HMCharacteristicTypeHardwareVersion: String

The hardware version of the accessory.

let HMCharacteristicTypeSoftwareVersion: String

The software version of the accessory.

let HMCharacteristicTypeLabelIndex: String

The index of the label for the service on an accessory with multiple instances of the same service.

let HMCharacteristicTypeLabelNamespace: String

The naming schema used to label the services on an accessory with multiple services of the same type.

let HMCharacteristicTypeActiveIdentifier: String

An index that maps to the current active Input Source service.

let HMCharacteristicTypeIdentifier: String

The identifier for an accessory.

let HMCharacteristicTypeInputDeviceType: String

The accessory input device type.

let HMCharacteristicTypeInputSourceType: String

The accessory input source type.

let HMCharacteristicTypeConfiguredName: String

A `UTF‑8` encoded user visible name on an accessory.

