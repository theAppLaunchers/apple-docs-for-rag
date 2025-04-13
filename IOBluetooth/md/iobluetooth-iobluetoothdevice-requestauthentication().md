

- IOBluetooth
- IOBluetoothDevice
-  requestAuthentication() 

Instance Method

# requestAuthentication()

Requests that the existing baseband connection be authenticated.

macOS

``` source
func requestAuthentication() -> IOReturn
```

## Return Value

Returns kIOReturnSuccess if the connection has been successfully been authenticated. Returns an error if authentication fails or no baseband connection exists.

## Discussion

In order to authenticate a baseband connection, a link key needs to be generated as a result of the pairing process. This call will synchronously initiate the pairing process with the target device and not return until the authentication process is complete. This API will be updated to allow for asynchronous operation.

