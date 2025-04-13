

- IOBluetooth
- OBEXFileTransferServices
-  disconnect() 

Instance Method

# disconnect()

Disconnect from the remote device

macOS

``` source
func disconnect() -> OBEXError
```

## Return Value

kOBEXSuccess, kOBEXSessionNotConnectedError, or kOBEXSessionBusyError initially. Further results returned through the fileTransferServicesDisconnectionComplete: delegate method if initially successful.

## Discussion

The user can manually disconnect the OBEXSession from the remote device if they want to. OBEXFileTransferServices will disconnect the OBEXSession at release only if it was responsible for opening the connection via a connect method.

