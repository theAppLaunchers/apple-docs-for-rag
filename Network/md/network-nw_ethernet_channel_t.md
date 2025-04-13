

- Network
-  nw_ethernet_channel_t 

Type Alias

# nw_ethernet_channel_t

An object you use to send and receive custom Ethernet frames.

iOS 12.0+iPadOS 12.0+Mac Catalyst 13.0+macOS 10.14+tvOS 12.0+visionOS 1.0+watchOS 6.0+

``` source
typealias nw_ethernet_channel_t = any OS_nw_ethernet_channel
```

## Discussion

Use Ethernet channels to send and receive custom Ethernet frame types over an interface.

Creating Ethernet channels requires the `com.apple.developer.networking.custom-protocol` entitlement.

## Topics

### Managing Ethernet Channels

func nw_ethernet_channel_create(UInt16, nw_interface_t) -> nw_ethernet_channel_t

Initializes an Ethernet channel on a specific interface with a custom Ethernet type.

func nw_ethernet_channel_set_queue(nw_ethernet_channel_t, dispatch_queue_t)

Sets the queue on which all channel events are delivered.

func nw_ethernet_channel_start(nw_ethernet_channel_t)

Starts the process of registering the channel.

func nw_ethernet_channel_cancel(nw_ethernet_channel_t)

Unregisters the channel from the interface.

### Handling State Updates

func nw_ethernet_channel_set_state_changed_handler(nw_ethernet_channel_t, nw_ethernet_channel_state_changed_handler_t?)

Sets a handler to receive channel state updates.

typealias nw_ethernet_channel_state_changed_handler_t

A handler that delivers Ethernet channel state updates with associated errors.

struct nw_ethernet_channel_state_t

States indicating whether an Ethernet channel is able to send and receive frames.

### Sending and Receiving Ethernet Frames

func nw_ethernet_channel_send(nw_ethernet_channel_t, dispatch_data_t, UInt16, UnsafeMutablePointer&lt;UInt8>, nw_ethernet_channel_send_completion_t)

Sends a single Ethernet frame over a channel to a specific Ethernet address.

typealias nw_ethernet_channel_send_completion_t

A handler that indicates when an Ethernet frame has been sent, or if an error was encountered.

func nw_ethernet_channel_set_receive_handler(nw_ethernet_channel_t, nw_ethernet_channel_receive_handler_t?)

Sets a handler to receive inbound Ethernet frames.

typealias nw_ethernet_channel_receive_handler_t

A handler that delivers inbound Ethernet frames.

typealias nw_ethernet_address_t

A 48-bit Ethernet address.

