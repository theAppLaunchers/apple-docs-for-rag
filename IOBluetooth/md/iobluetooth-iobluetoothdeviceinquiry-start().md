

- IOBluetooth
- IOBluetoothDeviceInquiry
-  start() 

Instance Method

# start()

Tells inquiry object to begin the inquiry and name updating process, if specified.

macOS

``` source
func start() -> IOReturn
```

## Return Value

Returns kIOReturnSuccess if start was successful. Returns kIOReturnBusy if the object is already in process. May return other IOReturn values, as appropriate.

## Discussion

Calling start multiple times in rapid succession or back-to-back will probably not produce the intended results. Inquiries are throttled if they are called too quickly in succession.

