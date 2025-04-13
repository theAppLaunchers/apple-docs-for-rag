

- Network
-  Network Data Types 

API Collection

# Network Data Types

## Topics

### Data Types

typealias nw_advertise_descriptor_t

A description used to advertise the Bonjour service that a listener provides.

typealias nw_browse_descriptor_t

A service description used to discover Bonjour services.

typealias nw_browse_result_change_t

Flags describing ways in which discovered services can change between specific results.

typealias nw_browse_result_enumerate_interface_t

A handler that enumerates the interfaces associated with a discovered service.

typealias nw_browse_result_t

A discovered service and metadata about the service.

typealias nw_browser_browse_results_changed_handler_t

A handler that delivers updates about discovered services.

typealias nw_browser_state_changed_handler_t

A handler that delivers browser state updates with associated errors.

typealias nw_browser_t

An object you use to browse for available network services.

typealias nw_connection_boolean_event_handler_t

A handler that receives Boolean state updates from a connection, such as viability and better path state.

typealias nw_connection_group_new_connection_handler_t

typealias nw_connection_group_receive_handler_t

A handler that receives inbound messages from members of the group.

typealias nw_connection_group_send_completion_t

A completion to notify you when data has been processed and sent.

typealias nw_connection_group_state_changed_handler_t

A handler that receives connection group state updates.

typealias nw_connection_group_t

An object you use to communicate with a group of endpoints, such as an IP multicast group on a local network.

typealias nw_connection_path_event_handler_t

A handler that delivers network path updates.

typealias nw_connection_receive_completion_t

A completion handler that indicates when content has been received by the connection, or that an error was encountered.

typealias nw_connection_send_completion_t

A completion handler that indicates when the connection has finished processing sent content.

typealias nw_connection_state_changed_handler_t

A handler that delivers connection state updates with associated errors.

typealias nw_connection_t

A bidirectional data connection between a local endpoint and a remote endpoint.

typealias nw_content_context_t

A representation of a message to send or receive, containing protocol metadata and send properties.

typealias nw_data_transfer_report_collect_block_t

A block that is delivered when a data transfer report is fully collected.

typealias nw_data_transfer_report_t

A report that provides metrics about data being sent and received on a connection.

typealias nw_endpoint_t

A local or remote endpoint in a network connection.

typealias nw_error_t

The errors returned by the Network framework.

typealias nw_establishment_report_access_block_t

A block that delivers a connection’s establishment report when it’s in the ready state.

typealias nw_establishment_report_t

A report that provides metrics about how a connection was established.

typealias nw_ethernet_address_t

A 48-bit Ethernet address.

typealias nw_ethernet_channel_receive_handler_t

A handler that delivers inbound Ethernet frames.

typealias nw_ethernet_channel_send_completion_t

A handler that indicates when an Ethernet frame has been sent, or if an error was encountered.

typealias nw_ethernet_channel_state_changed_handler_t

A handler that delivers Ethernet channel state updates with associated errors.

typealias nw_ethernet_channel_t

An object you use to send and receive custom Ethernet frames.

typealias nw_framer_block_t

A block to be invoked asynchronously on your framer protocol’s scheduling context.

typealias nw_framer_cleanup_handler_t

A handler that tells your protocol to clean up all allocations before being deallocated.

typealias nw_framer_input_handler_t

A handler that notifies your protocol that new inbound data is available to parse.

typealias nw_framer_message_dispose_value_t

A handler that’s invoked when your custom value needs to be released due to a message being released or the value being replaced.

typealias nw_framer_message_t

A message for a custom protocol, in which you can store arbitrary key-value pairs.

typealias nw_framer_output_handler_t

A handler that notifies your protocol about a new outbound message.

typealias nw_framer_parse_completion_t

A handler that examines a range of data being sent or received.

typealias nw_framer_start_handler_t

A handler that represents the entry point into your custom protocol.

typealias nw_framer_stop_handler_t

A handler that requests that your protocol send any final messages to close the connection.

typealias nw_framer_t

An object that represents a single instance of your custom protocol running in a connection.

typealias nw_framer_wakeup_handler_t

A handler that delivers a scheduled wakeup event.

typealias nw_group_descriptor_enumerate_endpoints_block_t

A handler that lists all endpoints added to the group descriptor.

typealias nw_group_descriptor_t

A type that defines a group of endpoints with which you can communicate, such as a multicast group.

typealias nw_interface_t

An interface that a network connection uses to send and receive data.

typealias nw_listener_advertised_endpoint_changed_handler_t

A handler that indicates changes to the service endpoints being advertised as they are added and removed.

typealias nw_listener_new_connection_group_handler_t

typealias nw_listener_new_connection_handler_t

A handler that delivers inbound connections.

typealias nw_listener_state_changed_handler_t

A handler that delivers listener state updates with associated errors.

typealias nw_listener_t

An object you use to listen for incoming network connections.

typealias nw_object_t

The generic type for objects in the Network framework.

typealias nw_path_enumerate_gateways_block_t

A block that enumerates the gateways configured on the interfaces available to a path.

typealias nw_path_enumerate_interfaces_block_t

A block that enumerates the interfaces available to a path.

typealias nw_path_monitor_cancel_handler_t

A handler that indicates when a monitor has been cancelled.

typealias nw_path_monitor_t

An observer that you use to monitor and react to network changes.

typealias nw_path_monitor_update_handler_t

A handler that delivers network path updates.

typealias nw_path_t

An object that contains information about the properties of the network that a connection uses, or that are available to your app.

typealias nw_protocol_metadata_t

The abstract superclass for specifying metadata about a network protocol.

typealias nw_proxy_domain_enumerator_t

typealias nw_report_protocol_enumerator_t

A block used to enumerate protocol handshakes performed during connection establishment.

typealias nw_report_resolution_enumerator_t

A block used to enumerate resolution steps performed during connection establishment.

typealias nw_report_resolution_report_enumerator_t

Iterates a list of resolution steps, as nw_resolution_report_t objects, performed during connection establishment, in order from first resolved to last resolved.

typealias nw_resolution_report_t

A description of a single DNS resolution step.

typealias nw_txt_record_access_bytes_t

A block that provides access to the raw bytes of a TXT record.

typealias nw_txt_record_access_key_t

A block that returns a value in a TXT record dictionary.

typealias nw_txt_record_applier_t

A block that iterates over values and keys in a TXT record dictionary.

typealias nw_txt_record_t

A dictionary representing a TXT record in a DNS packet.

typealias nw_ws_additional_header_enumerator_t

A block that enumerates additional HTTP headers in a WebSocket client request.

typealias nw_ws_client_request_handler_t

A handler that delivers inbound client handshake requests.

typealias nw_ws_pong_handler_t

A handler that indicates that a Pong message has been received for a previously sent Ping message, or that an error was encountered.

typealias nw_ws_request_t

A WebSocket handshake request sent from a client to a server.

typealias nw_ws_response_t

A WebSocket handshake reponse sent from a server to a client.

typealias nw_ws_subprotocol_enumerator_t

A block that enumerates the supported subprotocols in a WebSocket client request.

## See Also

### Reference

Network Constants

Access Network framework constants used in C.

Network Functions

Access Network framework functions used in C.

