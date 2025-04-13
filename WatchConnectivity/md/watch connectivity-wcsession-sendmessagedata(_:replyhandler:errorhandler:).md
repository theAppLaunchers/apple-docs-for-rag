

- Watch Connectivity
- WCSession
-  sendMessageData(\_:replyHandler:errorHandler:) 

Instance Method

# sendMessageData(\_:replyHandler:errorHandler:)

Sends a data object immediately to the paired and active device and optionally handles a response.

iOS 9.0+iPadOS 9.0+Mac Catalyst 9.0+visionOS 1.0+watchOS 2.0+

``` source
func sendMessageData(
    _ data: Data,
    replyHandler: ((Data) -> Void)?,
    errorHandler: ((any Error) -> Void)? = nil
)
```

## Parameters 

`data`  

A data object containing the information you want to send. This parameter must not be `nil`.

`replyHandler`  

A reply handler for receiving a response from the counterpart. Specify `nil` if you do not want to receive a reply. This block has no return value and takes the following parameter:

replyMessage  
A data object containing the response from the counterpart.

`errorHandler`  

A block that is executed when an error occurs. Specify `nil` if you do not care about error information. This block has no return value and takes the following parameter:

errorHandler  
An error object containing the reason for the failure. When sending messages, the most common error is that the paired device was not reachable, but other errors may occur too.

## Discussion

Use this message to send a data object to the counterpart as soon as possible. Messages are queued serially and delivered in the order in which you sent them. Delivery of the messages happens asynchronously, so this method returns immediately.

If you specify a reply handler block, your handler block is executed asynchronously on a background thread. The block is executed serially with respect to other incoming delegate messages.

Calling this method from your WatchKit extension while it is active and running wakes up the corresponding iOS app in the background and makes it reachable. Calling this method from your iOS app does not wake up the corresponding WatchKit extension. If you call this method and the counterpart is unreachable (or becomes unreachable before the message is delivered), the `errorHandler` block is executed with an appropriate error. The `errorHandler` block may also be called if the `message` parameter contains non property list data types.

This method can only be called while the session is active—that is, the activationState property is set to WCSessionActivationState.activated. Calling this method for an inactive or deactivated session is a programmer error.

## See Also

### Sending Messages

func sendMessage([String : Any], replyHandler: (([String : Any]) -> Void)?, errorHandler: ((any Error) -> Void)?)

Sends a message immediately to the paired and active device and optionally handles a response.

