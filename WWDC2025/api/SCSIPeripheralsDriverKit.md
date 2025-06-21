Framework

# SCSIPeripheralsDriverKit

Develop drivers for peripherals that use SCSI Block Command and Multimedia Command protocols.

DriverKit 22.0+

## [Overview](/documentation/SCSIPeripheralsDriverKit#overview)

The SCSIPeripheralsDriverKit framework supports the development of drivers for external devices that communicate using SCSI protocols. This framework operates at the logical unit level. For block-level driver development, use [BlockStorageDeviceDriverKit](/documentation/BlockStorageDeviceDriverKit). For protocol-level driver development, use [SCSIControllerDriverKit](/documentation/SCSIControllerDriverKit).

Develop your driver by subclassing [`IOUserSCSIPeripheralDeviceType00`](/documentation/scsiperipheralsdriverkit/iouserscsiperipheraldevicetype00) or [`IOUserSCSIPeripheralDeviceType05`](/documentation/scsiperipheralsdriverkit/iouserscsiperipheraldevicetype05), depending on whether your device works with SCSI Block Commands (SBC) or SCSI Multimedia Commands (SMC), respectively. In your subclass, override all methods the framework declares as pure virtual. Then package your driver in an app that uses the [System Extensions](/documentation/SystemExtensions) framework to install and upgrade the driver on the user’s Mac.

Note

SCSIPeripheralsDriverKit is available on macOS.

## [Topics](/documentation/SCSIPeripheralsDriverKit#topics)

### [Driver interfaces](/documentation/SCSIPeripheralsDriverKit#Driver-interfaces)

[`IOUserSCSIPeripheralDeviceType00`](/documentation/scsiperipheralsdriverkit/iouserscsiperipheraldevicetype00)

A DriverKit provider object that works with type 00 devices, those that use SCSI Block Commands (SBC).

[`IOUserSCSIPeripheralDeviceType05`](/documentation/scsiperipheralsdriverkit/iouserscsiperipheraldevicetype05)

A DriverKit provider object that works with type 05 devices, those that use SCSI Multimedia Commands (SMC).

### [Device commands](/documentation/SCSIPeripheralsDriverKit#Device-commands)

[

API Reference

SCSI commands](/documentation/scsiperipheralsdriverkit/scsi-commands)

Call the framework’s free functions to populate Command Descriptor Blocks (CDBs) to send to your peripheral.

### [Classes](/documentation/SCSIPeripheralsDriverKit#Classes)

[`IOUserSCSIPeripheralDeviceType07`](/documentation/scsiperipheralsdriverkit/iouserscsiperipheraldevicetype07)

### [Reference](/documentation/SCSIPeripheralsDriverKit#Reference)

[

API Reference

SCSIPeripheralsDriverKit Enumerations](/documentation/scsiperipheralsdriverkit/scsiperipheralsdriverkit-enumerations)

[

API Reference

SCSIPeripheralsDriverKit Data Types](/documentation/scsiperipheralsdriverkit/scsiperipheralsdriverkit-data-types)