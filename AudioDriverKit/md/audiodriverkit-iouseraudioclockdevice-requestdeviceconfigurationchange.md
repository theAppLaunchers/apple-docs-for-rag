

- AudioDriverKit
- IOUserAudioClockDevice
-  RequestDeviceConfigurationChange 

Instance Method

# RequestDeviceConfigurationChange

Instructs the host to initiate a configuration change operation.

DriverKit 21.0+

``` source
kern_return_t RequestDeviceConfigurationChange(uint64_t in_change_action, OSObject * in_change_info);
```

## Parameters 

`in_change_action`  

A uint64_t that indicates the action the device object takes. The invocation of PerformDeviceConfigurationChange passes this same action back to your driver. This value is purely for the driver’s use; the host doesn’t look at this value.

`in_change_info`  

A pointer to an OSObject containing information about the configuration change. The invocation of PerformDeviceConfigurationChange passes this same info back to your driver. This value is purely for the driver’s use; the host doesn’t look at this value.

## Return Value

kIOReturnSuccess on success, or another value if an error occurs. For a list of error codes, see Error Codes.

## Discussion

When an audio device object needs to change its structure or change any state related to I/O for any reason, begin by invoking this host method. The device object may not perform the state change until the host gives the device clearance to do so by invoking the driver’s `PerformDeviceConfigurationChange` method. Note that the host may defer the `PerformDeviceConfigurationChange` call to another thread at the host’s discretion.

The sorts of changes that must go through this mechanism includes anything that affects either the structure of the device or I/O. This includes, but isn’t limited to:

Changing stream layout.

Adding or removing controls.

Changing the nominal sample rate of the device.

Changing any sample formats on any stream on the device.

Changing the size of the ring buffer.

Changing presentation latency.

Changing the safety offset.

