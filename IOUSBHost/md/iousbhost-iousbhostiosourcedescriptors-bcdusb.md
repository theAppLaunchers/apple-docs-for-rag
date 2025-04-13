

- IOUSBHost
- IOUSBHostIOSourceDescriptors
-  bcdUSB 

Instance Property

# bcdUSB

The USB version that the device supports.

Mac Catalyst 14.0+macOS 10.15+

``` source
var bcdUSB: UInt16
```

## Discussion

Initialize this descriptor to the USB version that the device supports. Acceptable values are 0x0110, 0x0200, 0x0300, 0x0310.

## See Also

### Descriptors

var descriptor: IOUSBEndpointDescriptor

The descriptor for a USB endpoint.

var ssCompanionDescriptor: IOUSBSuperSpeedEndpointCompanionDescriptor

The descriptor for a SuperSpeed USB endpoint companion.

var sspCompanionDescriptor: IOUSBSuperSpeedPlusIsochronousEndpointCompanionDescriptor

The descriptor for a SuperSpeedPlus isochronous USB endpoint companion.

