

- XPC
-  xpc_connection_create(\_:\_:) 

Function

# xpc_connection_create(\_:\_:)

Creates a new connection object.

iOS 5.0+iPadOS 5.0+Mac Catalyst 13.1+macOS 10.7+

``` source
func xpc_connection_create(
    _ name: UnsafePointer?,
    _ targetq: dispatch_queue_t?
) -> xpc_connection_t
```

## Parameters 

`name`  

If non-`NULL`, the name of the service with which to connect. The returned connection will be a peer.

If `NULL`, an anonymous listener connection will be created. You can embed the ability to create new peer connections in an endpoint, which can be inserted into a message and sent to another process .

`targetq`  

The GCD queue to which the event handler block will be submitted. This parameter may be `NULL`, in which case the connection’s target queue will be the default target queue of `libdispatch`, defined as `DISPATCH_TARGET_QUEUE_DEFAULT`. The target queue may be changed later with a call to xpc_connection_set_target_queue(_:_:).

## Return Value

A new connection object. The caller is responsible for disposing of the returned object with xpc_release when it is no longer needed.

## Discussion

This method will succeed even if the named service does not exist. This is because the XPC namespace is not queried for the service name until the first call to xpc_connection_resume(_:).

XPC connections, like dispatch sources, are returned in a suspended state, so you must call xpc_connection_resume(_:) in order to begin receiving events from the connection. Also like dispatch sources, connections must be resumed in order to be safely released. It is a programming error to release a suspended connection.

## See Also

### Creation

typealias xpc_connection_t

A type that represents a connection to a named service.

func xpc_connection_create_from_endpoint(xpc_endpoint_t) -> xpc_connection_t

Creates a new connection from the specified endpoint.

func xpc_connection_create_mach_service(UnsafePointer&lt;CChar>, dispatch_queue_t?, UInt64) -> xpc_connection_t

Creates a new connection object that represents a Mach service.

func xpc_connection_set_target_queue(xpc_connection_t, dispatch_queue_t?)

Sets the target queue of the connection.

var XPC_CONNECTION_MACH_SERVICE_LISTENER: Int32

A flag that indicates the caller is the listener for the named service.

var XPC_CONNECTION_MACH_SERVICE_PRIVILEGED: Int32

A flag that indicates the job advertising the service name belongs to a launch daemon rather than a launch agent.

