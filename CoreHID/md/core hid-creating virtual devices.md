

- Core HID
-  Creating virtual devices 

Article

# Creating virtual devices

Use and interact with a virtual human interface device for testing and development.

## Overview

A virtual human interface device (HID) is a software implementation of a hardware device. The system treats the device as any other external peripheral. HIDVirtualDevice models a virtual device and you communicate with it using HIDDeviceClient. Use a virtual device to transport data back and forth between other apps without the need for a connected device.

Define the details of a HIDVirtualDevice by passing a set of HIDVirtualDevice.Properties during creation. You must pass descriptor and vendorID, and specify additional properties using init(descriptor:vendorID:productID:transport:product:manufacturer:modelNumber:versionNumber:serialNumber:uniqueID:locationID:localizationCode:extraProperties:).

The following creates a HIDVirtualDevice that acts as a keyboard:

```
// This describes a keyboard device according to the Human Interface Devices standard.
let keyboardDescriptor: Data = Data([0x05, 0x01, 0x09, 0x06, 0xA1, 0x01, 0x05, 0x07, 0x19, 0xE0, 0x29, 0xE7, 0x15, 0x00, 0x25, 0x01, 0x75, 0x01, 0x95, 0x08, 0x81, 0x02, 0x95, 0x01, 0x75, 0x08, 0x81, 0x01, 0x05, 0x08, 0x19, 0x01, 0x29, 0x05, 0x95, 0x05, 0x75, 0x01, 0x91, 0x02, 0x95, 0x01, 0x75, 0x03, 0x91, 0x01, 0x05, 0x07, 0x19, 0x00, 0x2A, 0xFF, 0x00, 0x95, 0x05, 0x75, 0x08, 0x15, 0x00, 0x26, 0xFF, 0x00, 0x81, 0x00, 0x05, 0xFF, 0x09, 0x03, 0x75, 0x08, 0x95, 0x01, 0x81, 0x02, 0xC0])
let properties = HIDVirtualDevice.Properties(descriptor: keyboardDescriptor, vendorID: 1)

guard let device = HIDVirtualDevice(properties: properties) else {
    return
}
```

The virtual device adopts the HIDVirtualDeviceDelegate protocol to process report requests. Clients on the system send set reports and receive get reports to and from this virtual device using dispatchSetReportRequest(type:id:data:timeout:) and dispatchGetReportRequest(type:id:timeout:):

```
final class Delegate : HIDVirtualDeviceDelegate {
    // A handler for system requests to send data to the device.
    func hidVirtualDevice(_ device: HIDVirtualDevice, receivedSetReportRequestOfType type: HIDReportType, id: HIDReportID?, data: Data) throws {
        print("Device received a set report request for report type:\(type) id:\(String(describing: id)) with data:[\(data.map { String(format: "%02x", $0) }.joined(separator: " "))]")
    }

    // A handler for system requests to query data from the device.
    func hidVirtualDevice(_ device: HIDVirtualDevice, receivedGetReportRequestOfType type: HIDReportType, id: HIDReportID?, maxSize: size_t) throws -> Data {
        print("Device received a get report request for report type:\(type) id:\(String(describing: id))")
        assert(maxSize >= 4)
        return (Data([1, 2, 3, 4]))
    }
}

await device.activate(delegate: Delegate())
```

The virtual device can also dispatch input reports to clients. This is similar to a keyboard dispatching data when a key is pressed.

```
// Send input data to the system to indicate device activity.
try await device.dispatchInputReport(data: Data([5, 6, 7, 8]), timestamp: SuspendingClock.now)
```

## See Also

### Simulation

actor HIDVirtualDevice

A virtual service to emulate a HID device connected to the system.

protocol HIDVirtualDeviceDelegate

The delegate to receive notifications for a virtual HID device.

struct Properties

The properties for a virtual HID device.

