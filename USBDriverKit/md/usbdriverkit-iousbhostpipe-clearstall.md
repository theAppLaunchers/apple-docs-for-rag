

- USBDriverKit
- IOUSBHostPipe
-  ClearStall 

Instance Method

# ClearStall

Clears the halt condition of the pipe.

DriverKit 19.0+

``` source
kern_return_t ClearStall(bool withRequest);
```

## Parameters 

`withRequest`  

A Boolean indicating whether to send a `CLEAR_FEATURE` request to the device with the value `ENDPOINT_HALT`. To keep the device’s data toggle synchronized with the host’s data toggle, it’s recommended that you specify true, but you may safely specify false for control endpoints. For information about this request, see section 9.4.1 of the USB 2.0 specification.

## Return Value

kIOReturnSuccess on success, or another value if an error occurs. See Error Codes.

## Discussion

When a bulk or interrupt USB endpoint encounters an I/O error other than a timeout, it transitions to a halted state that you must clear if you want to perform additional I/O on the endpoint. Call this method to clear the halted condition for the endpoint. This method aborts all pending I/O on the endpoint and resets its data toggle.

If an intermediate hub is between the device and your driver, this method also sends a `CLEAR_TT_BUFFER` control request (USB 2.0, section 11.24.2.3) to the hub.

## See Also

### Adjusting the Pipe’s Status

AdjustPipe

Adjusts the behavior of periodic endpoints to consume a different amount of bus bandwidth.

