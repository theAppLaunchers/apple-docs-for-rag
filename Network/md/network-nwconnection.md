

- Network
-  NWConnection 

Class

# NWConnection

A bidirectional data connection between a local endpoint and a remote endpoint.

iOS 12.0+iPadOS 12.0+Mac Catalyst 12.0+macOS 10.14+tvOS 12.0+visionOS 1.0+watchOS 5.0+

``` source
final class NWConnection
```

## Mentioned in 

Inspecting app activity data

## Topics

### Creating Connections

convenience init(host: NWEndpoint.Host, port: NWEndpoint.Port, using: NWParameters)

Initializes a new connection to a host and port.

init(to: NWEndpoint, using: NWParameters)

Initializes a new connection to a remote endpoint.

func start(queue: DispatchQueue)

Starts establishing a connection, and sets the queue on which to deliver all connection events.

func restart()

Restarts a connection that is in the waiting state.

### Handling State Updates

var state: NWConnection.State

The current state of the connection.

enum State

States indicating whether a connection can be used to send and receive data.

var stateUpdateHandler: ((NWConnection.State) -> Void)?

A handler that receives connection state updates.

### Sending and Receiving Data

func send(content: Data?, contentContext: NWConnection.ContentContext, isComplete: Bool, completion: NWConnection.SendCompletion)

Sends data on a connection.

func send&lt;Content>(content: Content?, contentContext: NWConnection.ContentContext, isComplete: Bool, completion: NWConnection.SendCompletion)

Sends data on a connection using a custom Data type.

enum SendCompletion

A completion handler that indicates when the connection has finished processing sent content.

func receive(minimumIncompleteLength: Int, maximumLength: Int, completion: (Data?, NWConnection.ContentContext?, Bool, NWError?) -> Void)

Schedules a single receive completion handler, with a range indicating how many bytes the handler can receive at one time.

func receiveMessage(completion: (Data?, NWConnection.ContentContext?, Bool, NWError?) -> Void)

Schedules a single receive completion handler for a complete message, as opposed to a range of bytes.

func batch(() -> Void)

Defines a block in which calls to send and receive are processed as a batch to improve performance.

class ContentContext

An object that represents a message to send or receive, containing protocol metadata and send properties.

var maximumDatagramSize: Int

The maximum size of a datagram message that can be sent on a connection.

### Canceling Connections

func cancel()

Cancels the connection and gracefully disconnects any established network protocols.

func forceCancel()

Cancels the connection and immediately disconnects any established network protocols.

func cancelCurrentEndpoint()

Causes the current endpoint to be rejected, allowing the connection to try another resolved address.

### Handling Path Updates

var currentPath: NWPath?

The network path the connection is using.

var pathUpdateHandler: ((NWPath) -> Void)?

A handler that receives network path updates.

var viabilityUpdateHandler: ((Bool) -> Void)?

A handler that receives updates when data can be sent and received.

var betterPathUpdateHandler: ((Bool) -> Void)?

A handler that receives updates when an alternative network path is preferred over the current path.

### Collecting Connection Metrics

Collecting Network Connection Metrics

Use reports to understand how DNS and protocol handshakes impact connection establishment.

func requestEstablishmentReport(queue: DispatchQueue, completion: (NWConnection.EstablishmentReport?) -> Void)

Requests a copy of the connection’s establishment report once the connection is in the ready state.

struct EstablishmentReport

A report that provides metrics about the establishment of a connection.

func startDataTransferReport() -> NWConnection.PendingDataTransferReport

Begins a new data transfer report, which can later be collected.

class PendingDataTransferReport

An outstanding data transfer report that has yet to be collected.

struct DataTransferReport

A report that provides metrics about data being sent and received on a connection.

### Inspecting Connections

func metadata(definition: NWProtocolDefinition) -> NWProtocolMetadata?

Retrieves the connection-wide metadata for a specific protocol.

class NWProtocolMetadata

The abstract superclass for specifying metadata about a network protocol.

let endpoint: NWEndpoint

The remote endpoint with which the connection was initialized.

let parameters: NWParameters

The parameters with which the connection was initialized.

var queue: DispatchQueue?

The queue on which connection events are delivered.

### Initializers

convenience init?(from: NWConnectionGroup, to: NWEndpoint?, using: NWProtocolOptions?)

convenience init?(message: NWConnectionGroup.Message)

### Instance Methods

func receiveDiscontiguous(minimumIncompleteLength: Int, maximumLength: Int, completion: (DispatchData?, NWConnection.ContentContext?, Bool, NWError?) -> Void)

func receiveMessageDiscontiguous(completion: (DispatchData?, NWConnection.ContentContext?, Bool, NWError?) -> Void)

## Relationships

### Conforms To

- CustomDebugStringConvertible
- Sendable

## See Also

### Connections and Listeners

class NWListener

An object you use to listen for incoming network connections.

class NWBrowser

An object you use to browse for available network services.

class NWConnectionGroup

An object you use to communicate with a group of endpoints, such as an IP multicast group on a local network.

class NWEthernetChannel

An object you use to send and receive custom Ethernet frames.

