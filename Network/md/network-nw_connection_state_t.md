

- Network
-  nw_connection_state_t 

Structure

# nw_connection_state_t

States indicating whether a connection can be used to send and receive data.

iOS 12.0+iPadOS 12.0+Mac Catalyst 13.0+macOS 10.14+tvOS 12.0+visionOS 1.0+watchOS 6.0+

``` source
struct nw_connection_state_t
```

## Topics

### Connection States

var nw_connection_state_invalid: nw_connection_state_t

The connection is not valid.

var nw_connection_state_waiting: nw_connection_state_t

The connection is waiting for a network path change.

var nw_connection_state_preparing: nw_connection_state_t

The connection in the process of being established.

var nw_connection_state_ready: nw_connection_state_t

The connection is established, and ready to send and receive data.

var nw_connection_state_failed: nw_connection_state_t

The connection has disconnected or encountered an error.

var nw_connection_state_cancelled: nw_connection_state_t

The connection has been canceled.

### Initializers

init(UInt32)

init(rawValue: UInt32)

### Instance Properties

var rawValue: UInt32

## Relationships

### Conforms To

- BitwiseCopyable
- Equatable
- Hashable
- RawRepresentable
- Sendable

## See Also

### C Network Structures

struct nw_connection_group_state_t

States that indicate whether you can use a connection group to send and receive messages.

struct nw_browser_state_t

States indicating whether a browser is able to discover services.

struct nw_data_transfer_report_state_t

States indicating whether a data transfer report is collected yet.

struct nw_endpoint_type_t

The type of a network endpoint, such as a host or a service.

struct nw_error_domain_t

The error domain for errors used by the Network framework.

struct nw_ethernet_channel_state_t

States indicating whether an Ethernet channel is able to send and receive frames.

struct nw_framer_start_result_t

Results that you send to indicate the disposition of your protocol after the start handler is invoked.

struct nw_interface_type_t

Types of network interfaces, based on their link layer media types.

struct nw_ip_ecn_flag_t

Flag values for Explicit Congestion Notifications in IP packets.

struct nw_ip_local_address_preference_t

Types of local addresses that can be selected, such as temporary or stable.

struct nw_ip_version_t

IP versions to require on connections and listeners.

struct nw_listener_state_t

States indicating whether a listener is able to accept incoming connections.

struct nw_multipath_service_t

Modes in which a connection can support multipath protocols.

struct nw_parameters_expired_dns_behavior_t

Options for configuring how expired DNS answers should be used.

struct nw_path_status_t

Status values indicating whether a path can be used by connections.

