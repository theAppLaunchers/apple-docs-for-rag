

- vmnet
-  vmnet_start_interface(\_:\_:\_:) 

Function

# vmnet_start_interface(\_:\_:\_:)

Starts host or shared mode on an interface with a specified configuration.

Mac Catalyst 13.0+macOS 10.10+

``` source
func vmnet_start_interface(
    _ interface_desc: xpc_object_t,
    _ queue: dispatch_queue_t,
    _ handler: @escaping vmnet_start_interface_completion_handler_t
) -> interface_ref?
```

## Parameters 

`interface_desc`  

An XPC dictionary describing parameters of the interface. Supported keys are described in interface_desc XPC Dictionary Keys.

`queue`  

The queue on which the handler is scheduled.

`handler`  

A block to be executed after interface is started.

- status: `vmnet` on success, or `vmnet` on failure.

- interface_param: On success, this argument contains an XPC dictionary containing information about the interface. Possible keys are described in interface_param XPC Dictionary Keys.

## Return Value

Returns an interface reference, or `NULL` if an error occurred.

## See Also

### Starting and Stopping Interfaces

func vmnet_interface_set_event_callback(interface_ref, interface_event_t, dispatch_queue_t?, vmnet_interface_event_callback_t?) -> vmnet_return_t

Schedules a callback to be executed when events for the specified interface are received.

func vmnet_stop_interface(interface_ref, dispatch_queue_t, vmnet_interface_completion_handler_t) -> vmnet_return_t

Stops the interface.

