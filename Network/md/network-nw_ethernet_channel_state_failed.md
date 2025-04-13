

- Network
-  nw_ethernet_channel_state_failed 

Global Variable

# nw_ethernet_channel_state_failed

The channel has encountered a fatal error.

iOS 12.0+iPadOS 12.0+Mac Catalyst 13.0+macOS 10.14+tvOS 12.0+visionOS 1.0+watchOS 6.0+

``` source
var nw_ethernet_channel_state_failed: nw_ethernet_channel_state_t { get }
```

## See Also

### States

var nw_ethernet_channel_state_invalid: nw_ethernet_channel_state_t

The channel is not valid.

var nw_ethernet_channel_state_waiting: nw_ethernet_channel_state_t

The channel is waiting for its interface to become available.

var nw_ethernet_channel_state_preparing: nw_ethernet_channel_state_t

The channel is registering with the interface.

var nw_ethernet_channel_state_ready: nw_ethernet_channel_state_t

The channel is able to send and receive Ethernet frames.

var nw_ethernet_channel_state_cancelled: nw_ethernet_channel_state_t

The channel has been canceled.

