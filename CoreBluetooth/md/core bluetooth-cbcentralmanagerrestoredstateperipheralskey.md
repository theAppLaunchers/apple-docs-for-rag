

- Core Bluetooth
-  CBCentralManagerRestoredStatePeripheralsKey 

Global Variable

# CBCentralManagerRestoredStatePeripheralsKey

An array of peripherals for use when restoring the state of a central manager.

iOS 7.0+iPadOS 7.0+Mac Catalyst 13.1+macOS 10.13+tvOS 9.0+visionOS 1.0+watchOS 2.0+

``` source
let CBCentralManagerRestoredStatePeripheralsKey: String
```

## Discussion

The value associated with this key is an NSArray of CBPeripheral objects. The array contains all of the peripherals connected to the central manager (or had a pending connection) at the time the system terminated the app.

When possible, the system restores all information about a peripheral, including any discovered services, characteristics, characteristic descriptors, and characteristic notification states.

## See Also

### State Restoration Options

let CBCentralManagerRestoredStateScanServicesKey: String

An array of service IDs for use when restoring state.

let CBCentralManagerRestoredStateScanOptionsKey: String

A dictionary of peripheral scan options for use when restoring state.

