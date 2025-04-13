

- IOBluetooth
- OBEXFileTransferServices
-  connectToObjectPushService() 

Instance Method

# connectToObjectPushService()

Connect to a remote device for ObjectPush operations. Most of the FTP functionality of this object will be disabled.

macOS

``` source
func connectToObjectPushService() -> OBEXError
```

## Return Value

kOBEXSuccess, kOBEXSessionBusyError, or kOBEXSessionAlreadyConnectedError, kOBEXNoResourcesError initially. Further results returned through the fileTransferServicesConnectionComplete: delegate method if initially successful.

## Discussion

If the OBEXSession given to OBEXFileTransferServices on creation is not connected it can be manually connected through this method.

