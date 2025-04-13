

- HIDDriverKit
-  Match Criteria 

# Match Criteria

Specify the criteria that the system uses to match your driver to a device.

## Overview

When the system detects a new device, it looks for drivers that match the device’s features and capabilities. You specify the features and capabilities that your driver supports using the `IOKitPersonalities` key of your driver’s `Info.plist` file. The `IOKitPersonalities` key contains the array of driver personality dictionaries, the keys of which correspond to device-specific attributes. For example, you might specify the HID usage types that your driver supports.

The keys below are constants defined in the `IOHIDDeviceKeys.h` header file of HIDDriverKit. To match against a specific key, include the value of the key in the personality dictionary. For example, to match against `kIOHIDPrimaryUsageKey`, include the `PrimaryUsage` string in your `Info.plist` file.

## Topics

### Manufacturer Keys

kIOHIDTransportKey

A key for specifying the transport mechanism of the device.

kIOHIDVendorIDKey

A key for specifying the vendor ID of the device.

kIOHIDProductIDKey

A key for specifying the product identifier of the device.

kIOHIDVersionNumberKey

A key for specifying the version number of the device.

kIOHIDManufacturerKey

A key that specifies the manufacturer of the device.

kIOHIDProductKey

A key that describes the product.

kIOHIDSerialNumberKey

A key that specifies the device's serial number.

### Location Keys

kIOHIDCountryCodeKey

A key that specifies the country code or region of the device.

kIOHIDLocationIDKey

A key that specifies the location ID of the device.

### Usage Keys

kIOHIDDeviceUsageKey

A key that specifies a usage type of the device.

kIOHIDDeviceUsagePageKey

A key that specifies a usage page of the device.

kIOHIDDeviceUsagePairsKey

A key that contains the top-level usages of the device.

kIOHIDPrimaryUsageKey

A key that specifies the primary usage type of the device.

kIOHIDPrimaryUsagePageKey

A key that specifies the primary usage page of the device.

## See Also

### HID Usage Tables

HID Usage Tables

Identify the types of data that HID devices can report to your driver.

