

- Network
-  nw_ip_metadata_set_service_class(\_:\_:) 

Function

# nw_ip_metadata_set_service_class(\_:\_:)

Sets a specific service class to mark on an IP packet.

iOS 12.0+iPadOS 12.0+Mac Catalyst 13.1+macOS 10.14+tvOS 12.0+visionOS 1.0+watchOS 5.0+

``` source
func nw_ip_metadata_set_service_class(
    _ metadata: nw_protocol_metadata_t,
    _ service_class: nw_service_class_t
)
```

## See Also

### Handling IP Packets

func nw_ip_create_metadata() -> nw_protocol_metadata_t

Initializes an IP packet configuration with default settings.

func nw_protocol_metadata_is_ip(nw_protocol_metadata_t) -> Bool

Checks whether a metadata object represents an IP packet.

func nw_ip_metadata_set_ecn_flag(nw_protocol_metadata_t, nw_ip_ecn_flag_t)

Sets a specific Explicit Congestion Notification flag value to set on an IP packet.

func nw_ip_metadata_get_ecn_flag(nw_protocol_metadata_t) -> nw_ip_ecn_flag_t

Checks the Explicit Congestion Notification flag value received on an IP packet.

struct nw_ip_ecn_flag_t

Flag values for Explicit Congestion Notifications in IP packets.

func nw_ip_metadata_get_service_class(nw_protocol_metadata_t) -> nw_service_class_t

Accesses a specific service class to mark on an IP packet.

func nw_ip_metadata_get_receive_time(nw_protocol_metadata_t) -> UInt64

Access the time at which a packet was received, in nanoseconds, based on `CLOCK_MONOTONIC_RAW`.

