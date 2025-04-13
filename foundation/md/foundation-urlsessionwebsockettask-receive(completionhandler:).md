

- Foundation
- URLSessionWebSocketTask
-  receive(completionHandler:) 

Instance Method

# receive(completionHandler:)

Reads a WebSocket message once all the frames of the message are available.

iOS 13.0+iPadOS 13.0+Mac Catalyst 13.0+macOS 10.15+tvOS 13.0+visionOS 1.0+watchOS 6.0+

``` source
@preconcurrency
func receive(completionHandler: @escaping (Result) -> Void)
```

## Parameters 

`completionHandler`  

A closure that receives two parameters: the WebSocket message, and an NSError that indicates an error encountered while receiving the message. The error is `nil` if no error occurred.

## Discussion

If the task reaches the maximumMessageSize while buffering the frames, this call fails with an error.

## See Also

### Sending and receiving data

func send(URLSessionWebSocketTask.Message, completionHandler: ((any Error)?) -> Void)

Sends a WebSocket message, receiving the result in a completion handler.

enum Message

An enumeration of the types of messages sent and received.

var maximumMessageSize: Int

The maximum number of bytes to buffer before the receive call fails with an error.

