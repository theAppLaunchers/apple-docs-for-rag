*   [XPC](/documentation/xpc)
*   XPCListener

Class

# XPCListener

A type that performs tasks for clients across process boundaries.

iOS 17.0+iPadOS 17.0+Mac Catalyst 17.0+macOS 14.0+tvOS 17.0+watchOS 10.0+

```swift
```swift
```swift
```swift
```swift
```swift
```swift
```swift
class XPCListener
```
```
```
```
```
```
```
```

## [Mentioned in](/documentation/XPC/XPCListener#mentions)

[

Creating XPC services](/documentation/xpc/creating-xpc-services)

## [Overview](/documentation/XPC/XPCListener#overview)

To implement an XPC service, create a listener and respond to incoming session requests.

## [Topics](/documentation/XPC/XPCListener#topics)

### [Creating a listener](/documentation/XPC/XPCListener#Creating-a-listener)

[`init(service: String, targetQueue: DispatchQueue?, options: XPCListener.InitializationOptions, incomingSessionHandler: (XPCListener.IncomingSessionRequest) -> XPCListener.IncomingSessionRequest.Decision) throws`](/documentation/xpc/xpclistener/init\(service:targetqueue:options:incomingsessionhandler:\))

Creates the server side of an XPC service using the specified service name.

```swift
```swift
```swift
struct InitializationOptions
```
```

Options that control the listener’s configuration, such as if it’s inactive at creation.
```
```swift
```swift
```swift
class IncomingSessionRequest
```
```

A session request from a client that you accept or reject.
```

### [Managing the life cycle](/documentation/XPC/XPCListener#Managing-the-life-cycle)

```swift
```swift
```swift
```swift
func activate() throws
```
```

Activates an inactive listener.
```
```swift
```swift
```swift
func cancel()
```
```

Cancels a listener.
```
```

### [Handling incoming messages](/documentation/XPC/XPCListener#Handling-incoming-messages)

```swift
```swift
```swift
```swift
protocol XPCPeerHandler
```
```

A type that handles incoming messages from a client and session cancellation.
```
```

### [Structures](/documentation/XPC/XPCListener#Structures)

```swift
```swift
```swift
```swift
struct Endpoint
```
```
```
```

### [Initializers](/documentation/XPC/XPCListener#Initializers)

[`convenience init(service: String, targetQueue: DispatchQueue?, options: XPCListener.InitializationOptions, requirement: XPCPeerRequirement, incomingSessionHandler: (XPCListener.IncomingSessionRequest) -> XPCListener.IncomingSessionRequest.Decision) throws`](/documentation/xpc/xpclistener/init\(service:targetqueue:options:requirement:incomingsessionhandler:\))

Creates a listener with the service defined by the provided name, and requires that the session peer has the specified requirement.

Beta

[`init(targetQueue: DispatchQueue?, options: XPCListener.InitializationOptions, incomingSessionHandler: (XPCListener.IncomingSessionRequest) -> XPCListener.IncomingSessionRequest.Decision)`](/documentation/xpc/xpclistener/init\(targetqueue:options:incomingsessionhandler:\))

Creates an anonymous listener

### [Instance Properties](/documentation/XPC/XPCListener#Instance-Properties)

```swift
```swift
```swift
```swift
var endpoint: XPCListener.Endpoint
```
```

Creates an endpoint from the listener.
```
```

## [Relationships](/documentation/XPC/XPCListener#relationships)

### [Conforms To](/documentation/XPC/XPCListener#conforms-to)

*   [`Copyable`](/documentation/Swift/Copyable)
*   [`CustomDebugStringConvertible`](/documentation/Swift/CustomDebugStringConvertible)
*   [`Sendable`](/documentation/Swift/Sendable)
*   [`SendableMetatype`](/documentation/Swift/SendableMetatype)

## [See Also](/documentation/XPC/XPCListener#see-also)

### [Interprocess communication](/documentation/XPC/XPCListener#Interprocess-communication)

[

Creating XPC services](/documentation/xpc/creating-xpc-services)

Configure a listener, establish a client session, and exchange messages between processes.

```swift
```swift
```swift
class XPCSession
```
```

A type that sends messages to a server process.
```
```swift
```swift
```swift
struct XPCReceivedMessage
```
```

A type that represents a message sent between a session and a listener.
```
```swift
```swift
```swift
typealias xpc_listener_t
```
```

A C type that performs tasks for clients across process boundaries.
```
```swift
```swift
```swift
typealias xpc_session_t
```
```

A C type that sends messages to a server process.
```