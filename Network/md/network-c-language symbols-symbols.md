

- Network
-  C-Language Symbols 

API Collection

# C-Language Symbols

## Topics

### C Network Structures

struct nw_connection_group_state_t

States that indicate whether you can use a connection group to send and receive messages.

struct nw_browser_state_t

States indicating whether a browser is able to discover services.

struct nw_connection_state_t

States indicating whether a connection can be used to send and receive data.

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

struct nw_report_resolution_protocol_t

A set of transport protocols connections use for DNS resolution.

struct nw_report_resolution_source_t

Sources that may provide DNS responses.

struct nw_service_class_t

Levels of service quality that can be used with a connection.

struct nw_txt_record_find_key_t

Status values describing what kind of value is stored in a TXT record dictionary.

struct nw_ws_close_code_t

Types of codes used upon closing a WebSocket connection.

struct nw_ws_opcode_t

Types of messages that you send and receive on a WebSocket connection.

struct nw_ws_response_status_t

Status values that are sent with a WebSocket server response.

struct nw_ws_version_t

Supported versions of the WebSocket protocol.

### C Network Protocols

protocol OS_nw_advertise_descriptor

protocol OS_nw_browse_descriptor

protocol OS_nw_browse_result

protocol OS_nw_browser

protocol OS_nw_connection

protocol OS_nw_connection_group

protocol OS_nw_content_context

protocol OS_nw_data_transfer_report

protocol OS_nw_endpoint

protocol OS_nw_error

protocol OS_nw_establishment_report

protocol OS_nw_ethernet_channel

protocol OS_nw_framer

protocol OS_nw_group_descriptor

protocol OS_nw_interface

protocol OS_nw_listener

protocol OS_nw_object

protocol OS_nw_parameters

protocol OS_nw_path

protocol OS_nw_path_monitor

protocol OS_nw_privacy_context

protocol OS_nw_protocol_definition

protocol OS_nw_protocol_metadata

protocol OS_nw_protocol_options

protocol OS_nw_protocol_stack

protocol OS_nw_proxy_config

protocol OS_nw_relay_hop

protocol OS_nw_resolution_report

protocol OS_nw_resolver_config

protocol OS_nw_txt_record

protocol OS_nw_ws_request

protocol OS_nw_ws_response

