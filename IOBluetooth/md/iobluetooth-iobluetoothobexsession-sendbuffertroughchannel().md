

- IOBluetooth
- IOBluetoothOBEXSession
-  sendBufferTroughChannel() 

Instance Method

# sendBufferTroughChannel()

Sends the next block of data through the rfcomm channel.

macOS

``` source
func sendBufferTroughChannel() -> IOReturn
```

## Discussion

Since a send in the rfcomm channel is broken in multiple write calls (this actually is true only if the size is grater than the rfcomm MTU). Each write call is performed by sendBufferTroughChannel. This should never need to be overwritten.

