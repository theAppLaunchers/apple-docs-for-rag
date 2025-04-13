

- XPC
-  xpc_connection_create_from_endpoint(\_:) 

Function

# xpc_connection_create_from_endpoint(\_:)

Creates a new connection from the specified endpoint.

iOS 5.0+iPadOS 5.0+Mac Catalyst 13.1+macOS 10.7+

``` source
func xpc_connection_create_from_endpoint(_ endpoint: xpc_endpoint_t) -> xpc_connection_t
```

## Parameters 

`endpoint`  

The endpoint from which to create the new connection.

## Return Value

A new peer connection to the listener represented by the given endpoint.

## Discussion

The same responsibilities of setting an event handler and resuming the connection after calling xpc_connection_create(_:_:) apply to the connection returned by this API. Since the connection yielded by this API is not associated with a name (and therefore is not rediscoverable), this connection will receive XPC_ERROR_CONNECTION_INVALID if the listening side crashes, exits or cancels the listener connection.

## See Also

### Creation

typealias xpc_connection_t

A type that represents a connection to a named service.

func xpc_connection_create(UnsafePointer&lt;CChar>?, dispatch_queue_t?) -> xpc_connection_t

Creates a new connection object.

func xpc_connection_create_mach_service(UnsafePointer&lt;CChar>, dispatch_queue_t?, UInt64) -> xpc_connection_t

Creates a new connection object that represents a Mach service.

func xpc_connection_set_target_queue(xpc_connection_t, dispatch_queue_t?)

Sets the target queue of the connection.

var XPC_CONNECTION_MACH_SERVICE_LISTENER: Int32

A flag that indicates the caller is the listener for the named service.

var XPC_CONNECTION_MACH_SERVICE_PRIVILEGED: Int32

A flag that indicates the job advertising the service name belongs to a launch daemon rather than a launch agent.

