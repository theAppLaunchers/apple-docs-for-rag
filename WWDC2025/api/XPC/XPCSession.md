*   [XPC](/documentation/xpc)
*   XPCSession

Class

# XPCSession

A type that sends messages to a server process.

iOS 17.0+iPadOS 17.0+Mac CatalystmacOS 14.0+tvOS 17.0+watchOS 10.0+

```swift
```swift
```swift
```swift
```swift
```swift
```swift
```swift
class XPCSession
```
```
```
```
```
```
```
```

## [Overview](/documentation/XPC/XPCSession#overview)

XPC sessions are stateful connections you use to send structured messages to a separate process. Once established, a session remains active until one side of the connection cancels it, at which point the system invalidates the connection.

## [Topics](/documentation/XPC/XPCSession#topics)

### [Creating a session](/documentation/XPC/XPCSession#Creating-a-session)

[`convenience init<Message>(xpcService: String, targetQueue: DispatchQueue?, options: XPCSession.InitializationOptions, incomingMessageHandler: ((Message) -> (any Encodable)?)?, cancellationHandler: ((XPCRichError) -> Void)?) throws`](/documentation/xpc/xpcsession/init\(xpcservice:targetqueue:options:incomingmessagehandler:cancellationhandler:\)-407h2)

Establishes a connection to an XPC service with the name and decodable message handler you specify.

[`convenience init(xpcService: String, targetQueue: DispatchQueue?, options: XPCSession.InitializationOptions, incomingMessageHandler: ((XPCReceivedMessage) -> (any Encodable)?)?, cancellationHandler: ((XPCRichError) -> Void)?) throws`](/documentation/xpc/xpcsession/init\(xpcservice:targetqueue:options:incomingmessagehandler:cancellationhandler:\)-9f4u0)

Establishes a connection to an XPC service with the name and received message handler you specify.

[`convenience init(xpcService: String, targetQueue: DispatchQueue?, options: XPCSession.InitializationOptions, incomingMessageHandler: ((XPCDictionary) -> XPCDictionary?)?, cancellationHandler: ((XPCRichError) -> Void)?) throws`](/documentation/xpc/xpcsession/init\(xpcservice:targetqueue:options:incomingmessagehandler:cancellationhandler:\)-bel3)

Establishes a connection to an XPC service with the name and dictionary message handler you specify.

[`convenience init(xpcService: String, targetQueue: DispatchQueue?, options: XPCSession.InitializationOptions, cancellationHandler: ((XPCRichError) -> Void)?) throws`](/documentation/xpc/xpcsession/init\(xpcservice:targetqueue:options:cancellationhandler:\))

Establishes a connection to an XPC service with the name you specify.

[`convenience init<Message>(machService: String, targetQueue: DispatchQueue?, options: XPCSession.InitializationOptions, incomingMessageHandler: ((Message) -> (any Encodable)?)?, cancellationHandler: ((XPCRichError) -> Void)?) throws`](/documentation/xpc/xpcsession/init\(machservice:targetqueue:options:incomingmessagehandler:cancellationhandler:\)-l3rz)

Establishes a connection to a launch agent or launch daemon with the name and decodable message handler you specify.

[`convenience init(machService: String, targetQueue: DispatchQueue?, options: XPCSession.InitializationOptions, incomingMessageHandler: ((XPCReceivedMessage) -> (any Encodable)?)?, cancellationHandler: ((XPCRichError) -> Void)?) throws`](/documentation/xpc/xpcsession/init\(machservice:targetqueue:options:incomingmessagehandler:cancellationhandler:\)-2xuyi)

Establishes a connection to a launch agent or launch daemon with the name and received message handler you specify.

[`convenience init(machService: String, targetQueue: DispatchQueue?, options: XPCSession.InitializationOptions, incomingMessageHandler: ((XPCDictionary) -> XPCDictionary?)?, cancellationHandler: ((XPCRichError) -> Void)?) throws`](/documentation/xpc/xpcsession/init\(machservice:targetqueue:options:incomingmessagehandler:cancellationhandler:\)-6jz7y)

Establishes a connection to a launch agent or launch daemon with the name and dictionary message handler you specify.

[`convenience init(machService: String, targetQueue: DispatchQueue?, options: XPCSession.InitializationOptions, cancellationHandler: ((XPCRichError) -> Void)?) throws`](/documentation/xpc/xpcsession/init\(machservice:targetqueue:options:cancellationhandler:\))

Establishes a connection to a launch agent or launch daemon with the name you specify.

```swift
```swift
```swift
struct InitializationOptions
```
```

Options that control the session’s configuration.
```
```swift
```swift
```swift
func setTargetQueue(DispatchQueue)
```
```

Sets the target dispatch queue on an inactive session for processing messages.
```

### [Managing the life cycle](/documentation/XPC/XPCSession#Managing-the-life-cycle)

```swift
```swift
```swift
```swift
func activate() throws
```
```

Activates a session so you can send messages.
```
```swift
```swift
```swift
func setIncomingMessageHandler<Message>((Message) -> (any Encodable)?)
```
```

Sets a closure to receive incoming decodable messages for a session.
```
```swift
```swift
```swift
func setIncomingMessageHandler((XPCReceivedMessage) -> (any Encodable)?)
```
```

Sets a closure to receive incoming received messages for a session.
```
```swift
```swift
```swift
func setIncomingMessageHandler((XPCDictionary) -> XPCDictionary?)
```
```

Sets a closure to receive incoming dictionary messages for a session.
```
```swift
```swift
```swift
func cancel(reason: String)
```
```

Cancels a session, discarding any unsent messages.
```
```swift
```swift
```swift
func setCancellationHandler((XPCRichError) -> Void)
```
```

Sets a closure the session calls when it’s canceled.
```
```

### [Sending messages](/documentation/XPC/XPCSession#Sending-messages)

```swift
```swift
```swift
```swift
func send<Message>(Message) throws
```
```

Sends an encodable message over the session to the destination service.
```
```swift
```swift
```swift
func send<Message>(Message, replyHandler: (Result<XPCReceivedMessage, XPCRichError>) -> Void) throws
```
```

Sends an encodable message over the session to the destination service, using the closure you specify to handle a reply and rich error.
```
```swift
```swift
```swift
func send<Message, Reply>(Message, replyHandler: (Result<Reply, any Error>) -> Void) throws
```
```

Sends an encodable message over the session to the destination service, using the closure you specify to handle a reply.
```
```swift
```swift
```swift
func send(message: XPCDictionary) throws
```
```

Sends a dictionary message over the session to the destination service.
```
```swift
```swift
```swift
func send(message: XPCDictionary, replyHandler: (Result<XPCDictionary, XPCRichError>) -> Void)
```
```

Sends a message asynchronously over the session to the destination service, calling a closure after receiving a reply.
```
```swift
```swift
```swift
func sendSync<Message>(Message) throws -> XPCReceivedMessage
```
```

Sends an encodable message over the session to the destination service, blocking the caller until receiving a reply message.
```
```swift
```swift
```swift
func sendSync<Message, Reply>(Message) throws -> Reply
```
```

Sends an encodable message over the session to the destination service, blocking the caller until receiving an encodable reply message.
```
```swift
```swift
```swift
func sendSync(message: XPCDictionary) throws -> XPCDictionary
```
```

Sends a dictionary message over the session to the destination service, blocking the caller until receiving a reply.
```
```

### [Initializers](/documentation/XPC/XPCSession#Initializers)

[`convenience init(endpoint: XPCListener.Endpoint, targetQueue: DispatchQueue?, options: XPCSession.InitializationOptions, cancellationHandler: ((XPCRichError) -> Void)?) throws`](/documentation/xpc/xpcsession/init\(endpoint:targetqueue:options:cancellationhandler:\))

Creates a new session object representing a connection to the xpc endpoint.

[`convenience init(endpoint: XPCListener.Endpoint, targetQueue: DispatchQueue?, options: XPCSession.InitializationOptions, incomingMessageHandler: ((XPCReceivedMessage) -> (any Encodable)?)?, cancellationHandler: ((XPCRichError) -> Void)?) throws`](/documentation/xpc/xpcsession/init\(endpoint:targetqueue:options:incomingmessagehandler:cancellationhandler:\)-1g0cc)

Creates a new session object representing a connection to the xpc endpoint.

[`convenience init<Message>(endpoint: XPCListener.Endpoint, targetQueue: DispatchQueue?, options: XPCSession.InitializationOptions, incomingMessageHandler: ((Message) -> (any Encodable)?)?, cancellationHandler: ((XPCRichError) -> Void)?) throws`](/documentation/xpc/xpcsession/init\(endpoint:targetqueue:options:incomingmessagehandler:cancellationhandler:\)-5coj9)

Creates a new session object representing a connection to the xpc endpoint.

[`convenience init(endpoint: XPCListener.Endpoint, targetQueue: DispatchQueue?, options: XPCSession.InitializationOptions, incomingMessageHandler: ((XPCDictionary) -> XPCDictionary?)?, cancellationHandler: ((XPCRichError) -> Void)?) throws`](/documentation/xpc/xpcsession/init\(endpoint:targetqueue:options:incomingmessagehandler:cancellationhandler:\)-63e2q)

Creates a new session object representing a connection to the xpc endpoint.

[`convenience init(machService: String, targetQueue: DispatchQueue?, options: XPCSession.InitializationOptions, requirement: XPCPeerRequirement, cancellationHandler: ((XPCRichError) -> Void)?) throws`](/documentation/xpc/xpcsession/init\(machservice:targetqueue:options:requirement:cancellationhandler:\))Beta

[`convenience init(machService: String, targetQueue: DispatchQueue?, options: XPCSession.InitializationOptions, requirement: XPCPeerRequirement, incomingMessageHandler: ((XPCDictionary) -> XPCDictionary?)?, cancellationHandler: ((XPCRichError) -> Void)?) throws`](/documentation/xpc/xpcsession/init\(machservice:targetqueue:options:requirement:incomingmessagehandler:cancellationhandler:\)-5pk9g)Beta

[`convenience init<Message>(machService: String, targetQueue: DispatchQueue?, options: XPCSession.InitializationOptions, requirement: XPCPeerRequirement, incomingMessageHandler: ((Message) -> (any Encodable)?)?, cancellationHandler: ((XPCRichError) -> Void)?) throws`](/documentation/xpc/xpcsession/init\(machservice:targetqueue:options:requirement:incomingmessagehandler:cancellationhandler:\)-7o5oq)Beta

[`convenience init(machService: String, targetQueue: DispatchQueue?, options: XPCSession.InitializationOptions, requirement: XPCPeerRequirement, incomingMessageHandler: ((XPCReceivedMessage) -> (any Encodable)?)?, cancellationHandler: ((XPCRichError) -> Void)?) throws`](/documentation/xpc/xpcsession/init\(machservice:targetqueue:options:requirement:incomingmessagehandler:cancellationhandler:\)-84ll1)Beta

[`convenience init(xpcService: String, targetQueue: DispatchQueue?, options: XPCSession.InitializationOptions, requirement: XPCPeerRequirement, cancellationHandler: ((XPCRichError) -> Void)?) throws`](/documentation/xpc/xpcsession/init\(xpcservice:targetqueue:options:requirement:cancellationhandler:\))

Creates a new session object representing a connection to the named service, and requires that the session peer has the specified requirement.

Beta

[`convenience init(xpcService: String, targetQueue: DispatchQueue?, options: XPCSession.InitializationOptions, requirement: XPCPeerRequirement, incomingMessageHandler: ((XPCDictionary) -> XPCDictionary?)?, cancellationHandler: ((XPCRichError) -> Void)?) throws`](/documentation/xpc/xpcsession/init\(xpcservice:targetqueue:options:requirement:incomingmessagehandler:cancellationhandler:\)-3p0jf)Beta

[`convenience init(xpcService: String, targetQueue: DispatchQueue?, options: XPCSession.InitializationOptions, requirement: XPCPeerRequirement, incomingMessageHandler: ((XPCReceivedMessage) -> (any Encodable)?)?, cancellationHandler: ((XPCRichError) -> Void)?) throws`](/documentation/xpc/xpcsession/init\(xpcservice:targetqueue:options:requirement:incomingmessagehandler:cancellationhandler:\)-6jxdc)Beta

[`convenience init<Message>(xpcService: String, targetQueue: DispatchQueue?, options: XPCSession.InitializationOptions, requirement: XPCPeerRequirement, incomingMessageHandler: ((Message) -> (any Encodable)?)?, cancellationHandler: ((XPCRichError) -> Void)?) throws`](/documentation/xpc/xpcsession/init\(xpcservice:targetqueue:options:requirement:incomingmessagehandler:cancellationhandler:\)-osu4)Beta

### [Instance Methods](/documentation/XPC/XPCSession#Instance-Methods)

```swift
```swift
```swift
```swift
func setPeerRequirement(XPCPeerRequirement)
```
```

Requires that the session peer has the specified requirement

Beta
```
```

## [Relationships](/documentation/XPC/XPCSession#relationships)

### [Conforms To](/documentation/XPC/XPCSession#conforms-to)

*   [`Copyable`](/documentation/Swift/Copyable)
*   [`CustomDebugStringConvertible`](/documentation/Swift/CustomDebugStringConvertible)
*   [`Sendable`](/documentation/Swift/Sendable)
*   [`SendableMetatype`](/documentation/Swift/SendableMetatype)

## [See Also](/documentation/XPC/XPCSession#see-also)

### [Interprocess communication](/documentation/XPC/XPCSession#Interprocess-communication)

[

Creating XPC services](/documentation/xpc/creating-xpc-services)

Configure a listener, establish a client session, and exchange messages between processes.

```swift
```swift
```swift
class XPCListener
```
```

A type that performs tasks for clients across process boundaries.
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