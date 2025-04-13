

- vmnet
-  vmnet_stop_interface(\_:\_:\_:) 

Function

# vmnet_stop_interface(\_:\_:\_:)

Stops the interface.

Mac Catalyst 13.0+macOS 10.10+

``` source
func vmnet_stop_interface(
    _ interface: interface_ref,
    _ queue: dispatch_queue_t,
    _ handler: @escaping vmnet_interface_completion_handler_t
) -> vmnet_return_t
```

## Parameters 

`interface`  

The interface reference.

`queue`  

The queue on which the handler is scheduled.

`handler`  

A block to be executed after interface is started.

- status: `vmnet` on success, or `vmnet` on failure.

## Return Value

Returns `vmnet` on success, or an error code on failure. See `vmnet` for possible values.

## Discussion

After this function is called, any further calls to read/write packets on `interface` will fail.

## See Also

### Starting and Stopping Interfaces

func vmnet_start_interface(xpc_object_t, dispatch_queue_t, vmnet_start_interface_completion_handler_t) -> interface_ref?

Starts host or shared mode on an interface with a specified configuration.

func vmnet_interface_set_event_callback(interface_ref, interface_event_t, dispatch_queue_t?, vmnet_interface_event_callback_t?) -> vmnet_return_t

Schedules a callback to be executed when events for the specified interface are received.

