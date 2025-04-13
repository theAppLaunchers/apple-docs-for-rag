

- Core Foundation
-  CFWriteStreamSetClient(\_:\_:\_:\_:) 

Function

# CFWriteStreamSetClient(\_:\_:\_:\_:)

Assigns a client to a stream, which receives callbacks when certain events occur.

iOSiPadOSMac CatalystmacOStvOSvisionOSwatchOS

``` source
func CFWriteStreamSetClient(
    _ stream: CFWriteStream!,
    _ streamEvents: CFOptionFlags,
    _ clientCB: CFWriteStreamClientCallBack!,
    _ clientContext: UnsafeMutablePointer!
) -> Bool
```

## Parameters 

`stream`  

The stream to modify.

`streamEvents`  

The set of events for which the client should receive callbacks. The events are listed in CFStreamEventType. If you pass kCFStreamEventNone, the current client for `stream` is removed.

`clientCB`  

The client callback function to call when one of the events requested in `streamEvents` occurs. If `NULL`, the current client for `stream` is removed.

`clientContext`  

A structure holding contextual information for the stream client. The function copies the information out of the structure, so the memory pointed to by `clientContext` does not need to persist beyond the function call. If `NULL`, the current client for `stream` is removed.

## Return Value

`true` if the stream supports asynchronous notification, `false` otherwise.

## Discussion

To avoid polling and blocking, you can register a client to hear about interesting events that occur on a stream. Only one client per stream is allowed; registering a new client replaces the previous one.

Once you have set a client, you need to schedule the stream in a run loop using CFWriteStreamScheduleWithRunLoop(_:_:_:) so that the client can receive the asynchronous notifications. You can schedule each stream in multiple run loops (for example, if you are using a thread pool). It is the caller’s responsibility to ensure that at least one of the scheduled run loops is being run, otherwise the callback cannot be called.

Although all Core Foundation streams currently support asynchronous notification, future stream types may not. If a stream does not support asynchronous notification, this function returns `false`. Typically, such streams never block for device I/O (for example, a stream writing to memory) and don’t benefit from asynchronous notification.

## See Also

### Setting Stream Properties

func CFWriteStreamSetProperty(CFWriteStream!, CFStreamPropertyKey!, CFTypeRef!) -> Bool

Sets the value of a property for a stream.

