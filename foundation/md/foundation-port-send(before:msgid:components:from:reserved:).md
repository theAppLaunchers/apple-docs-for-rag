

- Foundation
- Port
-  send(before:msgid:components:from:reserved:) 

Instance Method

# send(before:msgid:components:from:reserved:)

This method is provided for subclasses that have custom types of `NSPort`.

iOS 2.0+iPadOS 2.0+Mac Catalyst 13.0+macOS 10.0+tvOS 9.0+visionOS 1.0+watchOS 2.0+

``` source
func send(
    before limitDate: Date,
    msgid msgID: Int,
    components: NSMutableArray?,
    from receivePort: Port?,
    reserved headerSpaceReserved: Int
) -> Bool
```

## Parameters 

`limitDate`  

The last instant that a message may be sent.

`msgID`  

The message ID.

`components`  

The message components.

`receivePort`  

The receive port.

`headerSpaceReserved`  

The number of bytes reserved for the header.

## Discussion

`NSConnection` calls this method at the appropriate times. This method should not be called directly. This method could raise an `NSInvalidSendPortException`, `NSInvalidReceivePortException`, or an `NSPortSendException`, depending on the type of send port and the type of error.

## See Also

### Setting Information

func send(before: Date, components: NSMutableArray?, from: Port?, reserved: Int) -> Bool

This method is provided for subclasses that have custom types of `NSPort`.

var reservedSpaceLength: Int

The number of bytes of space reserved by the receiver for sending data.

