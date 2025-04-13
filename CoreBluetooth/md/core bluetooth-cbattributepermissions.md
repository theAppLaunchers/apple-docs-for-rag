

- Core Bluetooth
-  CBAttributePermissions 

Structure

# CBAttributePermissions

Values that represent the read, write, and encryption permissions for a characteristic’s value.

iOS 6.0+iPadOS 6.0+Mac Catalyst 13.1+macOS 10.9+tvOS 9.0+visionOS 1.0+watchOS 2.0+

``` source
struct CBAttributePermissions
```

## Overview

When you initialize a new mutable characteristic, you set the read, write, and encryption permissions for the characteristic’s value. Setting the read and write *permissions* for a characteristic’s value is different from specifying the read and write *properties* for a characteristic’s value. When you specify the read and write properties, the client (a central) inspects the read and write permissions of the characteristic’s value. When you specify the read and write permissions for a characteristic’s value, you set the permissions for the server (the peripheral) to allow the type of read or write specified by the characteristic’s properties. Therefore, when you initialize a mutable characteristic, you need to specify read or write properties and their corresponding permissions.

If you want to enforce encryption requirements for reads and writes on a characteristic’s value, you must specify the relevant permission (readEncryptionRequired or writeEncryptionRequired). You may set more than one permission for a characteristic’s value.

## Topics

### Creating a Permissions Instance

init(rawValue: UInt)

Creates a permissions instance from the provided raw value.

### Permissions

static var readable: CBAttributePermissions

A permission that indicates a peripheral can read the attribute’s value.

static var writeable: CBAttributePermissions

A permission that indicates a peripheral can write the attribute’s value.

static var readEncryptionRequired: CBAttributePermissions

A permission that indicates only trusted devices can read the attribute’s value.

static var writeEncryptionRequired: CBAttributePermissions

A permission that indicates only trusted devices can write the attribute’s value.

## Relationships

### Conforms To

- BitwiseCopyable
- Equatable
- ExpressibleByArrayLiteral
- OptionSet
- RawRepresentable
- Sendable
- SetAlgebra

## See Also

### Peripherals

class CBPeripheral

A remote peripheral device.

protocol CBPeripheralDelegate

A protocol that provides updates on the use of a peripheral’s services.

class CBPeripheralManager

An object that manages and advertises peripheral services exposed by this app.

protocol CBPeripheralManagerDelegate

A protocol that provides updates for local peripheral state and interactions with remote central devices.

class CBAttribute

A representation of common aspects of services offered by a peripheral.

