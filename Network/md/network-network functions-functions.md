

- Network
-  Network Functions 

API Collection

# Network Functions

Access Network framework functions used in C.

## Topics

### Functions

func nw_advertise_descriptor_copy_txt_record_object(nw_advertise_descriptor_t) -> nw_txt_record_t?

Accesses the TXT record to advertise with the service.

func nw_advertise_descriptor_create_application_service(UnsafePointer&lt;CChar>) -> nw_advertise_descriptor_t

func nw_advertise_descriptor_create_bonjour_service(UnsafePointer&lt;CChar>?, UnsafePointer&lt;CChar>, UnsafePointer&lt;CChar>?) -> nw_advertise_descriptor_t?

Initializes a Bonjour service to advertise.

func nw_advertise_descriptor_get_application_service_name(nw_advertise_descriptor_t) -> UnsafePointer&lt;CChar>?

func nw_advertise_descriptor_get_no_auto_rename(nw_advertise_descriptor_t) -> Bool

Checks whether the service prohibits automatic renaming in the event of a name conflict.

func nw_advertise_descriptor_set_no_auto_rename(nw_advertise_descriptor_t, Bool)

Sets a Boolean to indicate whether the service prohibits automatic renaming in the event of a name conflict.

func nw_advertise_descriptor_set_txt_record(nw_advertise_descriptor_t, UnsafeRawPointer?, Int)

Sets the TXT record as a raw buffer to advertise with the service.

func nw_advertise_descriptor_set_txt_record_object(nw_advertise_descriptor_t, nw_txt_record_t?)

Sets the TXT record to advertise with the service.

func nw_browse_descriptor_create_application_service(UnsafePointer&lt;CChar>) -> nw_browse_descriptor_t

func nw_browse_descriptor_create_bonjour_service(UnsafePointer&lt;CChar>, UnsafePointer&lt;CChar>?) -> nw_browse_descriptor_t

Initializes a service descriptor used to discover a Bonjour service.

func nw_browse_descriptor_get_application_service_name(nw_browse_descriptor_t) -> UnsafePointer&lt;CChar>?

func nw_browse_descriptor_get_bonjour_service_domain(nw_browse_descriptor_t) -> UnsafePointer&lt;CChar>?

Accesses the Bonjour service domain set on a browse descriptor.

func nw_browse_descriptor_get_bonjour_service_type(nw_browse_descriptor_t) -> UnsafePointer&lt;CChar>

Accesses the Bonjour service type set on a browse descriptor.

func nw_browse_descriptor_get_include_txt_record(nw_browse_descriptor_t) -> Bool

Checks if the browse descriptor requires including associated TXT records with all results.

func nw_browse_descriptor_set_include_txt_record(nw_browse_descriptor_t, Bool)

Requires including associated TXT records with all results generated for this service descriptor.

func nw_browse_result_copy_endpoint(nw_browse_result_t) -> nw_endpoint_t

The discovered service endpoint.

func nw_browse_result_copy_txt_record_object(nw_browse_result_t) -> nw_txt_record_t?

Accesses the TXT record associated with a discovered service.

func nw_browse_result_enumerate_interfaces(nw_browse_result_t, (nw_interface_t) -> Bool)

Enumerates the list of interfaces on which the service was discovered.

func nw_browse_result_get_changes(nw_browse_result_t?, nw_browse_result_t?) -> nw_browse_result_change_t

Compares two discovered services and calculates changes between them.

func nw_browse_result_get_interfaces_count(nw_browse_result_t) -> Int

Accesses the number of interfaces associated with a discovered service.

func nw_browser_cancel(nw_browser_t)

Stops browsing for services.

func nw_browser_copy_browse_descriptor(nw_browser_t) -> nw_browse_descriptor_t

Accesses the service descriptor with which the browser was created.

func nw_browser_copy_parameters(nw_browser_t) -> nw_parameters_t

Accesses the parameters with which the browser was created.

func nw_browser_create(nw_browse_descriptor_t, nw_parameters_t?) -> nw_browser_t

Initializes a browser with a type of service to discover.

func nw_browser_set_browse_results_changed_handler(nw_browser_t, nw_browser_browse_results_changed_handler_t?)

Sets the handler to receive updates about discovered services.

func nw_browser_set_queue(nw_browser_t, dispatch_queue_t)

Sets the queue on which all browser events will be delivered.

func nw_browser_set_state_changed_handler(nw_browser_t, nw_browser_state_changed_handler_t?)

Sets a handler to receive browser state updates.

func nw_browser_start(nw_browser_t)

Starts browsing for services.

func nw_connection_access_establishment_report(nw_connection_t, dispatch_queue_t, nw_establishment_report_access_block_t)

Requests a copy of the connection’s establishment report once the connection is in the ready state.

func nw_connection_batch(nw_connection_t, () -> Void)

Defines a block in which calls to send and receive are processed as a batch to improve performance.

func nw_connection_cancel(nw_connection_t)

Cancels the connection and gracefully disconnects any established network protocols.

func nw_connection_cancel_current_endpoint(nw_connection_t)

Causes the current endpoint to be rejected, allowing the connection to try another resolved address.

func nw_connection_copy_current_path(nw_connection_t) -> nw_path_t?

Accesses the network path the connection is using.

func nw_connection_copy_description(nw_connection_t) -> UnsafeMutablePointer&lt;CChar>

Copies the description of the connection as a string.

func nw_connection_copy_endpoint(nw_connection_t) -> nw_endpoint_t

Accesses the endpoint with which the connection was created.

func nw_connection_copy_parameters(nw_connection_t) -> nw_parameters_t

Accesses the parameters with which the connection was created.

func nw_connection_copy_protocol_metadata(nw_connection_t, nw_protocol_definition_t) -> nw_protocol_metadata_t?

Retrieves the connection-wide metadata for a specific protocol.

func nw_connection_create(nw_endpoint_t, nw_parameters_t) -> nw_connection_t

Initializes a new connection to a remote endpoint.

func nw_connection_create_new_data_transfer_report(nw_connection_t) -> nw_data_transfer_report_t

Begins a new data transfer report, which can later be collected.

func nw_connection_force_cancel(nw_connection_t)

Cancels the connection and immediately disconnects any established network protocols.

func nw_connection_get_maximum_datagram_size(nw_connection_t) -> UInt32

Accesses the maximum size of a datagram message that can be sent on a connection.

func nw_connection_group_cancel(nw_connection_group_t)

Cancels the connection group object and leaves the network group.

func nw_connection_group_copy_descriptor(nw_connection_group_t) -> nw_group_descriptor_t

Accesses the descriptor of the group you use to initialize the connection group.

func nw_connection_group_copy_local_endpoint_for_message(nw_connection_group_t, nw_content_context_t) -> nw_endpoint_t?

Accesses the local address and port you use to receive the message.

func nw_connection_group_copy_parameters(nw_connection_group_t) -> nw_parameters_t

Accesses the parameters with which you initialize the connection group.

func nw_connection_group_copy_path_for_message(nw_connection_group_t, nw_content_context_t) -> nw_path_t?

Accesses the network path on which you receive the message.

func nw_connection_group_copy_protocol_metadata(nw_connection_group_t, nw_protocol_definition_t) -> nw_protocol_metadata_t?

func nw_connection_group_copy_protocol_metadata_for_message(nw_connection_group_t, nw_content_context_t, nw_protocol_definition_t) -> nw_protocol_metadata_t?

func nw_connection_group_copy_remote_endpoint_for_message(nw_connection_group_t, nw_content_context_t) -> nw_endpoint_t?

Accesses the endpoint that originates the message you receive.

func nw_connection_group_create(nw_group_descriptor_t, nw_parameters_t) -> nw_connection_group_t

Initializes a new connection group with a group identifier.

func nw_connection_group_extract_connection(nw_connection_group_t, nw_endpoint_t?, nw_protocol_options_t?) -> nw_connection_t?

func nw_connection_group_extract_connection_for_message(nw_connection_group_t, nw_content_context_t) -> nw_connection_t?

Converts a message you receive from an endpoint into a connection object that you use for long-term communication with that endpoint.

func nw_connection_group_reinsert_extracted_connection(nw_connection_group_t, nw_connection_t) -> Bool

func nw_connection_group_reply(nw_connection_group_t, nw_content_context_t, nw_content_context_t, dispatch_data_t?)

Sends a reply to the specific endpoint that originates a group message you receive.

func nw_connection_group_send_message(nw_connection_group_t, dispatch_data_t?, nw_endpoint_t?, nw_content_context_t, nw_connection_group_send_completion_t)

Sends data to the entire group, or to a specific member of the group.

func nw_connection_group_set_new_connection_handler(nw_connection_group_t, nw_connection_group_new_connection_handler_t?)

func nw_connection_group_set_queue(nw_connection_group_t, dispatch_queue_t)

Sets the queue on which you handle connection group events.

func nw_connection_group_set_receive_handler(nw_connection_group_t, UInt32, Bool, nw_connection_group_receive_handler_t?)

Sets a handler that receives inbound messages from members of the group.

func nw_connection_group_set_state_changed_handler(nw_connection_group_t, nw_connection_group_state_changed_handler_t?)

Sets a handler that receives connection group state updates.

func nw_connection_group_start(nw_connection_group_t)

Joins the group and registers to receive messages.

func nw_connection_receive(nw_connection_t, UInt32, UInt32, nw_connection_receive_completion_t)

Schedules a single receive completion handler, with a range indicating how many bytes the handler can receive at one time.

func nw_connection_receive_message(nw_connection_t, nw_connection_receive_completion_t)

Schedules a single receive completion handler for a complete message, as opposed to a range of bytes.

func nw_connection_restart(nw_connection_t)

Restarts a connection that is in the waiting state.

func nw_connection_send(nw_connection_t, dispatch_data_t?, nw_content_context_t, Bool, nw_connection_send_completion_t)

Sends data on a connection.

func nw_connection_set_better_path_available_handler(nw_connection_t, nw_connection_boolean_event_handler_t?)

Sets a handler that receives updates when an alternative network path is preferred over the current path.

func nw_connection_set_path_changed_handler(nw_connection_t, nw_connection_path_event_handler_t?)

Sets a handler that receives network path updates.

func nw_connection_set_queue(nw_connection_t, dispatch_queue_t)

Sets the queue on which all connection events are delivered.

func nw_connection_set_state_changed_handler(nw_connection_t, nw_connection_state_changed_handler_t?)

Sets a handler to receive connection state updates.

func nw_connection_set_viability_changed_handler(nw_connection_t, nw_connection_boolean_event_handler_t?)

Sets a handler that receives updates when data can be sent and received.

func nw_connection_start(nw_connection_t)

Starts establishing a connection.

func nw_content_context_copy_antecedent(nw_content_context_t) -> nw_content_context_t?

Accesses the optional message context that must be sent before the context you are sending.

func nw_content_context_copy_protocol_metadata(nw_content_context_t, nw_protocol_definition_t) -> nw_protocol_metadata_t?

Retreives the metadata associated with a specific protocol.

func nw_content_context_create(UnsafePointer&lt;CChar>) -> nw_content_context_t

Initializes a custom message context.

func nw_content_context_foreach_protocol_metadata(nw_content_context_t, (nw_protocol_definition_t, nw_protocol_metadata_t) -> Void)

Iterates through all protocol metadata associated with the message context.

func nw_content_context_get_expiration_milliseconds(nw_content_context_t) -> UInt64

Accesses the expiration set for this message context.

func nw_content_context_get_identifier(nw_content_context_t) -> UnsafePointer&lt;CChar>

Accesses the identifier used to create this message context.

func nw_content_context_get_is_final(nw_content_context_t) -> Bool

Checks whether this context represents the final message being received.

func nw_content_context_get_relative_priority(nw_content_context_t) -> Double

Accesses the relative value of priority used to reorder contexts when sending.

func nw_content_context_set_antecedent(nw_content_context_t, nw_content_context_t?)

Set an optional message context that must be sent before the context you are sending.

func nw_content_context_set_expiration_milliseconds(nw_content_context_t, UInt64)

Sets the number of milliseconds after which sending the data associated with this context must begin, otherwise the data is discarded.

func nw_content_context_set_is_final(nw_content_context_t, Bool)

Sets a Boolean indicating if this context represents the final message being sent.

func nw_content_context_set_metadata_for_protocol(nw_content_context_t, nw_protocol_metadata_t)

Sets protocol metadata to configure per-message or per-packet properties.

func nw_content_context_set_relative_priority(nw_content_context_t, Double)

Sets the relative value of priority used to reorder contexts when sending.

func nw_data_transfer_report_collect(nw_data_transfer_report_t, dispatch_queue_t, nw_data_transfer_report_collect_block_t)

Stops an outstanding data transfer report and calculates the results.

func nw_data_transfer_report_copy_path_interface(nw_data_transfer_report_t, UInt32) -> nw_interface_t

Accesses the network interface the path used.

func nw_data_transfer_report_get_duration_milliseconds(nw_data_transfer_report_t) -> UInt64

Checks the duration of the data transfer report, from when it was started to when it was collected.

func nw_data_transfer_report_get_path_count(nw_data_transfer_report_t) -> UInt32

Checks the number of valid paths in the report.

func nw_data_transfer_report_get_path_radio_type(nw_data_transfer_report_t, UInt32) -> nw_interface_radio_type_t

func nw_data_transfer_report_get_received_application_byte_count(nw_data_transfer_report_t, UInt32) -> UInt64

Accesses the number of bytes the connection delivered.

func nw_data_transfer_report_get_received_ip_packet_count(nw_data_transfer_report_t, UInt32) -> UInt64

Accesses the number of IP packets the connection received.

func nw_data_transfer_report_get_received_transport_byte_count(nw_data_transfer_report_t, UInt32) -> UInt64

Accesses the number of bytes the transport protocol delivered.

func nw_data_transfer_report_get_received_transport_duplicate_byte_count(nw_data_transfer_report_t, UInt32) -> UInt64

Accesses the number of duplicated bytes the transport protocol detected.

func nw_data_transfer_report_get_received_transport_out_of_order_byte_count(nw_data_transfer_report_t, UInt32) -> UInt64

Accesses the number of bytes the transport protocol received out of order.

func nw_data_transfer_report_get_sent_application_byte_count(nw_data_transfer_report_t, UInt32) -> UInt64

Accesses the number of bytes sent on the connection.

func nw_data_transfer_report_get_sent_ip_packet_count(nw_data_transfer_report_t, UInt32) -> UInt64

Accesses the number of IP packets the connection sent.

func nw_data_transfer_report_get_sent_transport_byte_count(nw_data_transfer_report_t, UInt32) -> UInt64

Accesses the number of bytes sent into the transport protocol.

func nw_data_transfer_report_get_sent_transport_retransmitted_byte_count(nw_data_transfer_report_t, UInt32) -> UInt64

Accesses the number of bytes the transport protocol retransmitted.

func nw_data_transfer_report_get_state(nw_data_transfer_report_t) -> nw_data_transfer_report_state_t

Checks whether a data transfer report is collected.

func nw_data_transfer_report_get_transport_minimum_rtt_milliseconds(nw_data_transfer_report_t, UInt32) -> UInt64

Accesses the minimum round-trip time the transport protocol measured, in milliseconds.

func nw_data_transfer_report_get_transport_rtt_variance(nw_data_transfer_report_t, UInt32) -> UInt64

Accesses the variance of the round-trip time the transport protocol measured.

func nw_data_transfer_report_get_transport_smoothed_rtt_milliseconds(nw_data_transfer_report_t, UInt32) -> UInt64

Accesses the smoothed round-trip time the transport protocol measured, in milliseconds.

func nw_endpoint_copy_address_string(nw_endpoint_t) -> UnsafeMutablePointer&lt;CChar>

Copies the address of an endpoint as a string.

func nw_endpoint_copy_port_string(nw_endpoint_t) -> UnsafeMutablePointer&lt;CChar>

Copies the port of an endpoint as a string.

func nw_endpoint_copy_txt_record(nw_endpoint_t) -> nw_txt_record_t?

func nw_endpoint_create_address(UnsafePointer&lt;sockaddr>) -> nw_endpoint_t

Creates a network endpoint with an address structure.

func nw_endpoint_create_bonjour_service(UnsafePointer&lt;CChar>, UnsafePointer&lt;CChar>, UnsafePointer&lt;CChar>) -> nw_endpoint_t

Creates a network endpoint with a Bonjour service name, type, and domain.

func nw_endpoint_create_host(UnsafePointer&lt;CChar>, UnsafePointer&lt;CChar>) -> nw_endpoint_t

Creates a network endpoint with a hostname and port, where the hostname may be interpreted as an IP address.

func nw_endpoint_create_url(UnsafePointer&lt;CChar>) -> nw_endpoint_t

Creates a network endpoint with a URL string.

func nw_endpoint_get_address(nw_endpoint_t) -> UnsafePointer&lt;sockaddr>

Accesses the address structure stored in an address endpoint.

func nw_endpoint_get_bonjour_service_domain(nw_endpoint_t) -> UnsafePointer&lt;CChar>

Accesses the Bonjour service domain stored in an endpoint.

func nw_endpoint_get_bonjour_service_name(nw_endpoint_t) -> UnsafePointer&lt;CChar>

Accesses the Bonjour service name stored in an endpoint.

func nw_endpoint_get_bonjour_service_type(nw_endpoint_t) -> UnsafePointer&lt;CChar>

Accesses the Bonjour service type stored in an endpoint.

func nw_endpoint_get_hostname(nw_endpoint_t) -> UnsafePointer&lt;CChar>

Accesses the hostname stored in an endpoint.

func nw_endpoint_get_port(nw_endpoint_t) -> UInt16

Accesses the port stored in an endpoint, in host-byte order.

func nw_endpoint_get_signature(nw_endpoint_t, UnsafeMutablePointer&lt;Int>) -> UnsafePointer&lt;UInt8>?

func nw_endpoint_get_type(nw_endpoint_t) -> nw_endpoint_type_t

Accesses the type of a endpoint.

func nw_endpoint_get_url(nw_endpoint_t) -> UnsafePointer&lt;CChar>

Accesses the URL string stored in an endpoint.

func nw_error_copy_cf_error(nw_error_t) -> Unmanaged&lt;CFError>

Returns a copy of a network error.

func nw_error_get_error_code(nw_error_t) -> Int32

Accesses the specific code of the network error.

func nw_error_get_error_domain(nw_error_t) -> nw_error_domain_t

Accesses the domain of the network error.

func nw_establishment_report_copy_proxy_endpoint(nw_establishment_report_t) -> nw_endpoint_t?

Accesses the endpoint of the proxy the connection used.

func nw_establishment_report_enumerate_protocols(nw_establishment_report_t, (nw_protocol_definition_t, UInt64, UInt64) -> Bool)

Iterates a list of protocol handshakes in order from first completed to last completed.

func nw_establishment_report_enumerate_resolution_reports(nw_establishment_report_t, (nw_resolution_report_t) -> Bool)

func nw_establishment_report_enumerate_resolutions(nw_establishment_report_t, (nw_report_resolution_source_t, UInt64, UInt32, nw_endpoint_t, nw_endpoint_t) -> Bool)

Iterates a list of resolution steps performed during connection establishment, in order from first resolved to last resolved.

func nw_establishment_report_get_attempt_started_after_milliseconds(nw_establishment_report_t) -> UInt64

Accesses the time between the call to start and the beginning of the successful connection attempt, in milliseconds.

func nw_establishment_report_get_duration_milliseconds(nw_establishment_report_t) -> UInt64

Checks the total duration of the successful connection establishment attempt, from the preparing state to the ready state.

func nw_establishment_report_get_previous_attempt_count(nw_establishment_report_t) -> UInt32

Checks the number of attempts made before the successful attempt, when the connection moved from the preparing state back to the waiting state.

func nw_establishment_report_get_proxy_configured(nw_establishment_report_t) -> Bool

Checks whether a proxy was configured on the connection.

func nw_establishment_report_get_used_proxy(nw_establishment_report_t) -> Bool

Checks whether the connection used a proxy.

func nw_ethernet_channel_cancel(nw_ethernet_channel_t)

Unregisters the channel from the interface.

func nw_ethernet_channel_create(UInt16, nw_interface_t) -> nw_ethernet_channel_t

Initializes an Ethernet channel on a specific interface with a custom Ethernet type.

func nw_ethernet_channel_create_with_parameters(UInt16, nw_interface_t, nw_parameters_t) -> nw_ethernet_channel_t

func nw_ethernet_channel_get_maximum_payload_size(nw_ethernet_channel_t) -> UInt32

func nw_ethernet_channel_send(nw_ethernet_channel_t, dispatch_data_t, UInt16, UnsafeMutablePointer&lt;UInt8>, nw_ethernet_channel_send_completion_t)

Sends a single Ethernet frame over a channel to a specific Ethernet address.

func nw_ethernet_channel_set_queue(nw_ethernet_channel_t, dispatch_queue_t)

Sets the queue on which all channel events are delivered.

func nw_ethernet_channel_set_receive_handler(nw_ethernet_channel_t, nw_ethernet_channel_receive_handler_t?)

Sets a handler to receive inbound Ethernet frames.

func nw_ethernet_channel_set_state_changed_handler(nw_ethernet_channel_t, nw_ethernet_channel_state_changed_handler_t?)

Sets a handler to receive channel state updates.

func nw_ethernet_channel_start(nw_ethernet_channel_t)

Starts the process of registering the channel.

func nw_framer_async(nw_framer_t, nw_framer_block_t)

Requests that a block be executed on the connection’s internal scheduling context.

func nw_framer_copy_local_endpoint(nw_framer_t) -> nw_endpoint_t

Accesses the local endpoint of the connection in which your protocol is running.

func nw_framer_copy_options(nw_framer_t) -> nw_protocol_options_t

func nw_framer_copy_parameters(nw_framer_t) -> nw_parameters_t

Accesses the parameters of the connection in which your protocol is running.

func nw_framer_copy_remote_endpoint(nw_framer_t) -> nw_endpoint_t

Accesses the remote endpoint of the connection in which your protocol is running.

func nw_framer_create_definition(UnsafePointer&lt;CChar>, UInt32, nw_framer_start_handler_t) -> nw_protocol_definition_t

Initializes a new protocol definition based on your protocol implementation.

func nw_framer_create_options(nw_protocol_definition_t) -> nw_protocol_options_t

Initializes a set of protocol options with a custom framer definition.

func nw_framer_deliver_input(nw_framer_t, UnsafePointer&lt;UInt8>, Int, nw_framer_message_t, Bool)

Delivers an inbound message containing arbitrary data from your protocol to the application.

func nw_framer_deliver_input_no_copy(nw_framer_t, Int, nw_framer_message_t, Bool) -> Bool

Delivers an inbound message containing a specific number of next received bytes.

func nw_framer_mark_failed_with_error(nw_framer_t, Int32)

Indicates to a connection that your protocol has encountered an error, or has gracefully closed.

func nw_framer_mark_ready(nw_framer_t)

Indicates to a connection that your protocol’s handshake is complete.

func nw_framer_message_access_value(nw_framer_message_t, UnsafePointer&lt;CChar>, (UnsafeRawPointer?) -> Bool) -> Bool

Accesses a custom value stored in a framer message.

func nw_framer_message_copy_object_value(nw_framer_message_t, UnsafePointer&lt;CChar>) -> Any?

Accesses an NSObject value stored in a framer message.

func nw_framer_message_create(nw_framer_t) -> nw_framer_message_t

Initializes an empty message from within a framer implementation.

func nw_framer_message_set_object_value(nw_framer_message_t, UnsafePointer&lt;CChar>, Any?)

Sets an NSObject value to be stored in a framer message.

func nw_framer_message_set_value(nw_framer_message_t, UnsafePointer&lt;CChar>, UnsafeMutableRawPointer?, nw_framer_message_dispose_value_t?)

Sets a value to be stored in a framer message, with a completion to call to disposed the stored value when the message is released.

func nw_framer_options_copy_object_value(nw_protocol_options_t, UnsafePointer&lt;CChar>) -> Any?

func nw_framer_options_set_object_value(nw_protocol_options_t, UnsafePointer&lt;CChar>, Any?)

func nw_framer_parse_input(nw_framer_t, Int, Int, UnsafeMutablePointer&lt;UInt8>?, (UnsafeMutablePointer&lt;UInt8>?, Int, Bool) -> Int) -> Bool

Examines the content of input data while inside your input handler block.

func nw_framer_parse_output(nw_framer_t, Int, Int, UnsafeMutablePointer&lt;UInt8>?, (UnsafeMutablePointer&lt;UInt8>?, Int, Bool) -> Int) -> Bool

Examines the content of output data while inside your output handler.

func nw_framer_pass_through_input(nw_framer_t)

Indicates that your protocol no longer needs to handle input data.

func nw_framer_pass_through_output(nw_framer_t)

Indicates that your protocol no longer needs to handle output data.

func nw_framer_prepend_application_protocol(nw_framer_t, nw_protocol_options_t) -> Bool

Dynamically adds another protocol that will run above your protocol after your protocol calls nw_framer_mark_ready(_:).

func nw_framer_protocol_create_message(nw_protocol_definition_t) -> nw_framer_message_t

Initializes an empty message for a custom framer definition.

func nw_framer_schedule_wakeup(nw_framer_t, UInt64)

Requests that the nw_framer_wakeup_handler_t be called on your protocol at a specific time in the future.

func nw_framer_set_cleanup_handler(nw_framer_t, nw_framer_cleanup_handler_t)

Sets a block to handle the final cleanup of allocations made by your protocol instance.

func nw_framer_set_input_handler(nw_framer_t, nw_framer_input_handler_t)

Sets a block to handle new inbound data.

func nw_framer_set_output_handler(nw_framer_t, nw_framer_output_handler_t)

Sets a block to handle new outbound messages.

func nw_framer_set_stop_handler(nw_framer_t, nw_framer_stop_handler_t)

Sets a block to handle when the connection is being closed.

func nw_framer_set_wakeup_handler(nw_framer_t, nw_framer_wakeup_handler_t)

Sets a handler to receive scheduled wakeup events.

func nw_framer_write_output(nw_framer_t, UnsafePointer&lt;UInt8>, Int)

Sends arbitrary output data in a buffer from your protocol to the next protocol.

func nw_framer_write_output_data(nw_framer_t, dispatch_data_t)

Sends arbitrary output data from your protocol to the next protocol.

func nw_framer_write_output_no_copy(nw_framer_t, Int) -> Bool

Sends a specific number of bytes from a message while inside your output handler.

func nw_group_descriptor_add_endpoint(nw_group_descriptor_t, nw_endpoint_t) -> Bool

Adds a multicast address endpoint you specify to define an extra IP multicast group to join.

func nw_group_descriptor_create_multicast(nw_endpoint_t) -> nw_group_descriptor_t

Creates group descriptor you use to join an IP multicast group on a local network.

func nw_group_descriptor_create_multiplex(nw_endpoint_t) -> nw_group_descriptor_t

func nw_group_descriptor_enumerate_endpoints(nw_group_descriptor_t, (nw_endpoint_t) -> Bool)

Sets a handler to list all endpoints added to the group descriptor.

func nw_interface_get_index(nw_interface_t) -> UInt32

Accesses the system interface index associated with the interface.

func nw_interface_get_name(nw_interface_t) -> UnsafePointer&lt;CChar>

Accesses the name of the interface.

func nw_interface_get_type(nw_interface_t) -> nw_interface_type_t

Accesses the type of the interface, such as Wi-Fi or Loopback.

func nw_ip_create_metadata() -> nw_protocol_metadata_t

Initializes an IP packet configuration with default settings.

func nw_ip_metadata_get_ecn_flag(nw_protocol_metadata_t) -> nw_ip_ecn_flag_t

Checks the Explicit Congestion Notification flag value received on an IP packet.

func nw_ip_metadata_get_receive_time(nw_protocol_metadata_t) -> UInt64

Access the time at which a packet was received, in nanoseconds, based on `CLOCK_MONOTONIC_RAW`.

func nw_ip_metadata_get_service_class(nw_protocol_metadata_t) -> nw_service_class_t

Accesses a specific service class to mark on an IP packet.

func nw_ip_metadata_set_ecn_flag(nw_protocol_metadata_t, nw_ip_ecn_flag_t)

Sets a specific Explicit Congestion Notification flag value to set on an IP packet.

func nw_ip_metadata_set_service_class(nw_protocol_metadata_t, nw_service_class_t)

Sets a specific service class to mark on an IP packet.

func nw_ip_options_set_calculate_receive_time(nw_protocol_options_t, Bool)

Configures a connection to deliver receive timestamps for IP packets.

func nw_ip_options_set_disable_fragmentation(nw_protocol_options_t, Bool)

Configures a connection to disable fragmentation on outbound packets.

func nw_ip_options_set_disable_multicast_loopback(nw_protocol_options_t, Bool)

func nw_ip_options_set_hop_limit(nw_protocol_options_t, UInt8)

Configures the default hop limit for packets generated by a connection.

func nw_ip_options_set_local_address_preference(nw_protocol_options_t, nw_ip_local_address_preference_t)

Configures a connection to prefer certain types of local addresses, such as temporary or stable.

func nw_ip_options_set_use_minimum_mtu(nw_protocol_options_t, Bool)

Configures a connection to use the minimum MTU value, which is 1280 bytes for IPv6.

func nw_ip_options_set_version(nw_protocol_options_t, nw_ip_version_t)

Sets a required IP version to disable all other versions for a connection.

func nw_listener_cancel(nw_listener_t)

Stops listening for inbound connections.

func nw_listener_create(nw_parameters_t) -> nw_listener_t?

Initializes a network listener, which will select a random port.

func nw_listener_create_with_connection(nw_connection_t, nw_parameters_t) -> nw_listener_t?

Initializes a network listener to receive new streams on a multiplexed connection.

func nw_listener_create_with_launchd_key(nw_parameters_t, UnsafePointer&lt;CChar>) -> nw_listener_t

func nw_listener_create_with_port(UnsafePointer&lt;CChar>, nw_parameters_t) -> nw_listener_t?

Initializes a network listener with a specified local port.

func nw_listener_get_new_connection_limit(nw_listener_t) -> UInt32

Checks the remaining number of inbound connections to deliver before rejecting connections.

func nw_listener_get_port(nw_listener_t) -> UInt16

The port on which the listener can accept connections.

func nw_listener_set_advertise_descriptor(nw_listener_t, nw_advertise_descriptor_t?)

Sets a Bonjour service that advertises the listener on the local network.

func nw_listener_set_advertised_endpoint_changed_handler(nw_listener_t, nw_listener_advertised_endpoint_changed_handler_t?)

Sets a handler that receives updates for the service endpoint being advertised.

func nw_listener_set_new_connection_group_handler(nw_listener_t, nw_listener_new_connection_group_handler_t?)

func nw_listener_set_new_connection_handler(nw_listener_t, nw_listener_new_connection_handler_t?)

Sets a handler that receives inbound connections.

func nw_listener_set_new_connection_limit(nw_listener_t, UInt32)

Resets the number of inbound connections to deliver before rejecting connections.

func nw_listener_set_queue(nw_listener_t, dispatch_queue_t)

Sets the queue on which all listener events are delivered.

func nw_listener_set_state_changed_handler(nw_listener_t, nw_listener_state_changed_handler_t?)

Sets a handler to receive listener state updates.

func nw_listener_start(nw_listener_t)

Registers for listening for inbound connections.

func nw_multicast_group_descriptor_get_disable_unicast_traffic(nw_group_descriptor_t) -> Bool

Checks a Boolean that indicates whether a connection group should reject unicast traffic.

func nw_multicast_group_descriptor_set_disable_unicast_traffic(nw_group_descriptor_t, Bool)

Sets a Boolean that indicates whether a connection group should reject unicast traffic.

func nw_multicast_group_descriptor_set_specific_source(nw_group_descriptor_t, nw_endpoint_t)

Sets an optional address endpoint used to filter received multicast packets.

func nw_parameters_create_application_service() -> nw_parameters_t

func nw_parameters_create_quic(nw_parameters_configure_protocol_block_t) -> nw_parameters_t

Initializes parameters for QUIC connections and listeners.

func nw_parameters_requires_dnssec_validation(nw_parameters_t) -> Bool

Checks whether a connection requires DNSSEC validation when resolving endpoints.

func nw_parameters_set_requires_dnssec_validation(nw_parameters_t, Bool)

Determines whether a connection requires DNSSEC validation when resolving endpoints.

func nw_path_copy_effective_local_endpoint(nw_path_t) -> nw_endpoint_t?

Accesses the local endpoint in use by a connection’s network path.

func nw_path_copy_effective_remote_endpoint(nw_path_t) -> nw_endpoint_t?

Accesses the remote endpoint in use by a connection’s network path.

func nw_path_enumerate_gateways(nw_path_t, (nw_endpoint_t) -> Bool)

Enumerates the list of gateways configured on the interfaces available to a path.

func nw_path_enumerate_interfaces(nw_path_t, (nw_interface_t) -> Bool)

Enumerates the list of all interfaces available to the path, in order of preference.

func nw_path_get_status(nw_path_t) -> nw_path_status_t

Checks whether a path can be used by connections.

func nw_path_get_unsatisfied_reason(nw_path_t) -> nw_path_unsatisfied_reason_t

func nw_path_has_dns(nw_path_t) -> Bool

Checks whether the path has a DNS server configured.

func nw_path_has_ipv4(nw_path_t) -> Bool

Checks whether the path can route IPv4 traffic.

func nw_path_has_ipv6(nw_path_t) -> Bool

Checks whether the path can route IPv6 traffic.

func nw_path_is_constrained(nw_path_t) -> Bool

Checks whether the path uses an interface in Low Data Mode.

func nw_path_is_equal(nw_path_t, nw_path_t) -> Bool

Compares if two paths are identical.

func nw_path_is_expensive(nw_path_t) -> Bool

Checks whether the path uses an interface that is considered expensive, such as Cellular or a Personal Hotspot.

func nw_path_monitor_cancel(nw_path_monitor_t)

Stops receiving network path updates.

func nw_path_monitor_create() -> nw_path_monitor_t

Initializes a path monitor to observe all available interface types.

func nw_path_monitor_create_for_ethernet_channel() -> nw_path_monitor_t

func nw_path_monitor_create_with_type(nw_interface_type_t) -> nw_path_monitor_t

Initializes a path monitor to observe a specific interface type.

func nw_path_monitor_prohibit_interface_type(nw_path_monitor_t, nw_interface_type_t)

Prohibit a path monitor from using a specific interface type.

func nw_path_monitor_set_cancel_handler(nw_path_monitor_t, nw_path_monitor_cancel_handler_t)

Sets a handler to determine when a monitor is fully cancelled and will no longer deliver events.

func nw_path_monitor_set_queue(nw_path_monitor_t, dispatch_queue_t)

Sets a queue on which to deliver path events.

func nw_path_monitor_set_update_handler(nw_path_monitor_t, nw_path_monitor_update_handler_t)

Sets a handler to receive network path updates.

func nw_path_monitor_start(nw_path_monitor_t)

Starts monitoring path changes.

func nw_path_uses_interface_type(nw_path_t, nw_interface_type_t) -> Bool

Checks if connections using the path may send traffic over a specific interface type.

func nw_protocol_copy_ip_definition() -> nw_protocol_definition_t

Accesses the system definition of the Internet Protocol.

func nw_protocol_copy_quic_definition() -> nw_protocol_definition_t

Accesses the system definition of the QUIC transport protocol.

func nw_protocol_copy_tcp_definition() -> nw_protocol_definition_t

Accesses the system definition of the Transport Control Protocol.

func nw_protocol_copy_tls_definition() -> nw_protocol_definition_t

Accesses the system definition of the Transport Layer Security protocol.

func nw_protocol_copy_udp_definition() -> nw_protocol_definition_t

Accesses the system definition of the User Datagram Protocol.

func nw_protocol_copy_ws_definition() -> nw_protocol_definition_t

Accesses the system definition of the WebSocket protocol.

func nw_protocol_metadata_copy_definition(nw_protocol_metadata_t) -> nw_protocol_definition_t

Accesses the protocol definition associated with the metadata object.

func nw_protocol_metadata_is_framer_message(nw_protocol_metadata_t) -> Bool

Checks if a metadata object represents a custom framer protocol message.

func nw_protocol_metadata_is_ip(nw_protocol_metadata_t) -> Bool

Checks whether a metadata object represents an IP packet.

func nw_protocol_metadata_is_quic(nw_protocol_metadata_t) -> Bool

Checks whether a metadata object contains QUIC connection state.

func nw_protocol_metadata_is_tcp(nw_protocol_metadata_t) -> Bool

Checks whether a metadata object contains TCP connection state.

func nw_protocol_metadata_is_tls(nw_protocol_metadata_t) -> Bool

Checks whether a metadata object contains TLS connection state.

func nw_protocol_metadata_is_udp(nw_protocol_metadata_t) -> Bool

Checks whether a metadata object represents a UDP datagram.

func nw_protocol_metadata_is_ws(nw_protocol_metadata_t) -> Bool

Checks whether a metadata object represents a WebSocket message.

func nw_protocol_options_is_quic(nw_protocol_options_t) -> Bool

Checks whether an options object uses the QUIC protocol.

func nw_proxy_config_add_excluded_domain(nw_proxy_config_t, UnsafePointer&lt;CChar>)

func nw_proxy_config_add_match_domain(nw_proxy_config_t, UnsafePointer&lt;CChar>)

func nw_proxy_config_clear_excluded_domains(nw_proxy_config_t)

func nw_proxy_config_clear_match_domains(nw_proxy_config_t)

func nw_proxy_config_enumerate_excluded_domains(nw_proxy_config_t, (UnsafePointer&lt;CChar>) -> Void)

func nw_proxy_config_enumerate_match_domains(nw_proxy_config_t, (UnsafePointer&lt;CChar>) -> Void)

func nw_quic_add_tls_application_protocol(nw_protocol_options_t, UnsafePointer&lt;CChar>)

Adds a supported Application-Layer Protocol Negotiation value.

func nw_quic_copy_sec_protocol_metadata(nw_protocol_metadata_t) -> sec_protocol_metadata_t

Accesses the result of the QUIC handshake.

func nw_quic_copy_sec_protocol_options(nw_protocol_options_t) -> sec_protocol_options_t

Accesses the handshake security options QUIC will use.

func nw_quic_create_options() -> nw_protocol_options_t

Initializes a default set of QUIC connection options.

func nw_quic_get_application_error(nw_protocol_metadata_t) -> UInt64

Accesses the QUIC application error code received from the peer.

func nw_quic_get_application_error_reason(nw_protocol_metadata_t) -> UnsafePointer&lt;CChar>?

Accesses the QUIC application error reason received from the peer.

func nw_quic_get_idle_timeout(nw_protocol_options_t) -> UInt32

Accesses the idle timeout for the QUIC connection, in milliseconds.

func nw_quic_get_initial_max_data(nw_protocol_options_t) -> UInt64

Accesses a QUIC connection’s initial maximum data transport parameter.

func nw_quic_get_initial_max_stream_data_bidirectional_local(nw_protocol_options_t) -> UInt64

Accesses a QUIC connection’s initial maximum stream data limit for locally-initiated bidirectional streams.

func nw_quic_get_initial_max_stream_data_bidirectional_remote(nw_protocol_options_t) -> UInt64

Accesses a QUIC connection’s initial maximum stream data limit for remote-initiated bidirectional streams.

func nw_quic_get_initial_max_stream_data_unidirectional(nw_protocol_options_t) -> UInt64

Accesses a QUIC connection’s initial maximum stream data limit for unidirectional streams.

func nw_quic_get_initial_max_streams_bidirectional(nw_protocol_options_t) -> UInt64

Accesses a QUIC connection’s initial maximum number of bidirectional streams.

func nw_quic_get_initial_max_streams_unidirectional(nw_protocol_options_t) -> UInt64

Accesses a QUIC connection’s initial maximum number of unidirectional streams.

func nw_quic_get_keepalive_interval(nw_protocol_metadata_t) -> UInt16

Accesses the keepalive interval for the QUIC connection, in seconds.

func nw_quic_get_local_max_streams_bidirectional(nw_protocol_metadata_t) -> UInt64

Accesses the maximum number of bidirectional streams that the peer can create on a QUIC connection.

func nw_quic_get_local_max_streams_unidirectional(nw_protocol_metadata_t) -> UInt64

Accesses the maximum number of unidirectional streams that the peer can create on a QUIC connection.

func nw_quic_get_max_datagram_frame_size(nw_protocol_options_t) -> UInt16

Accesses a QUIC connection’s maximum DATAGRAM frame size.

func nw_quic_get_max_udp_payload_size(nw_protocol_options_t) -> UInt16

Accesses the maximum length of a QUIC packet that can be received on a connection, in bytes.

func nw_quic_get_remote_idle_timeout(nw_protocol_metadata_t) -> UInt64

Accesses the idle timeout value from the peer’s transport parameters, in milliseconds.

func nw_quic_get_remote_max_streams_bidirectional(nw_protocol_metadata_t) -> UInt64

Accesses the maximum number of bidirectional streams advertised by peer that the connection is allowed to create.

func nw_quic_get_remote_max_streams_unidirectional(nw_protocol_metadata_t) -> UInt64

Accesses the maximum number of unidirectional streams advertised by peer that the connection is allowed to create.

func nw_quic_get_stream_application_error(nw_protocol_metadata_t) -> UInt64

Accesses the QUIC application error code received from the peer for the stream.

func nw_quic_get_stream_id(nw_protocol_metadata_t) -> UInt64

Accesses the QUIC stream identifier.

func nw_quic_get_stream_is_datagram(nw_protocol_options_t) -> Bool

Checks if a QUIC stream is a datagram flow, instead of a byte stream.

func nw_quic_get_stream_is_unidirectional(nw_protocol_options_t) -> Bool

Checks if a QUIC stream is unidirectional, instead of bidirectional.

func nw_quic_get_stream_type(nw_protocol_metadata_t) -> UInt8

Accesses the stream type of the QUIC stream.

func nw_quic_get_stream_usable_datagram_frame_size(nw_protocol_metadata_t) -> UInt16

Accesses the maximum usable size of a datagram frame on a QUIC datagram flow.

func nw_quic_set_application_error(nw_protocol_metadata_t, UInt64, UnsafePointer&lt;CChar>?)

Sets the QUIC application error code to send for the connection.

func nw_quic_set_idle_timeout(nw_protocol_options_t, UInt32)

Sets the idle timeout for the QUIC connection, in milliseconds.

func nw_quic_set_initial_max_data(nw_protocol_options_t, UInt64)

Sets a QUIC connection’s initial maximum data transport parameter.

func nw_quic_set_initial_max_stream_data_bidirectional_local(nw_protocol_options_t, UInt64)

Sets a QUIC connection’s initial maximum stream data limit for locally-initiated bidirectional streams.

func nw_quic_set_initial_max_stream_data_bidirectional_remote(nw_protocol_options_t, UInt64)

Sets a QUIC connection’s initial maximum stream data limit for remote-initiated bidirectional streams.

func nw_quic_set_initial_max_stream_data_unidirectional(nw_protocol_options_t, UInt64)

Sets a QUIC connection’s initial maximum stream data limit for unidirectional streams.

func nw_quic_set_initial_max_streams_bidirectional(nw_protocol_options_t, UInt64)

Sets a QUIC connection’s initial maximum number of bidirectional streams.

func nw_quic_set_initial_max_streams_unidirectional(nw_protocol_options_t, UInt64)

Sets a QUIC connection’s initial maximum number of unidirectional streams.

func nw_quic_set_keepalive_interval(nw_protocol_metadata_t, UInt16)

Sets the keepalive interval for the QUIC connection, in seconds.

func nw_quic_set_local_max_streams_bidirectional(nw_protocol_metadata_t, UInt64)

Sets the maximum number of bidirectional streams that the peer can create on a QUIC connection.

func nw_quic_set_local_max_streams_unidirectional(nw_protocol_metadata_t, UInt64)

Sets the maximum number of unidirectional streams that the peer can create on a QUIC connection.

func nw_quic_set_max_datagram_frame_size(nw_protocol_options_t, UInt16)

Sets a QUIC connection’s maximum DATAGRAM frame size.

func nw_quic_set_max_udp_payload_size(nw_protocol_options_t, UInt16)

Sets the maximum length of a QUIC packet that can be received on a connection, in bytes.

func nw_quic_set_stream_application_error(nw_protocol_metadata_t, UInt64)

Sets the QUIC application error code to send for the stream.

func nw_quic_set_stream_is_datagram(nw_protocol_options_t, Bool)

Configures a QUIC stream as a datagram flow, instead of a byte stream.

func nw_quic_set_stream_is_unidirectional(nw_protocol_options_t, Bool)

Configures a QUIC stream as unidirectional, instead of bidirectional.

func nw_resolution_report_copy_preferred_endpoint(nw_resolution_report_t) -> nw_endpoint_t

Accesses the resolved endpoint that the connection used for its first connection attempt.

func nw_resolution_report_copy_successful_endpoint(nw_resolution_report_t) -> nw_endpoint_t

Accesses the resolved endpoint that led to the established connection.

func nw_resolution_report_get_endpoint_count(nw_resolution_report_t) -> UInt32

Accesses the number of endpoints resolved in this step.

func nw_resolution_report_get_milliseconds(nw_resolution_report_t) -> UInt64

Accesses the duration of this resolution step, from when the query was issued to when the response was complete.

func nw_resolution_report_get_protocol(nw_resolution_report_t) -> nw_report_resolution_protocol_t

Accesses the transport protocol your connection used for DNS resolution.

func nw_resolution_report_get_source(nw_resolution_report_t) -> nw_report_resolution_source_t

Accesses the source of the DNS response.

func nw_tcp_create_options() -> nw_protocol_options_t

Initializes a default set of TCP connection options.

func nw_tcp_get_available_receive_buffer(nw_protocol_metadata_t) -> UInt32

Accesses the number of available bytes in the TCP receive buffer.

func nw_tcp_get_available_send_buffer(nw_protocol_metadata_t) -> UInt32

Accesses the number of available bytes in the TCP send buffer.

func nw_tcp_options_set_connection_timeout(nw_protocol_options_t, UInt32)

Sets the number of seconds that TCP waits before timing out its handshake.

func nw_tcp_options_set_disable_ack_stretching(nw_protocol_options_t, Bool)

Disables TCP acknowledgment stretching.

func nw_tcp_options_set_disable_ecn(nw_protocol_options_t, Bool)

Disables negotiation of Explicit Congestion Notification markings.

func nw_tcp_options_set_enable_fast_open(nw_protocol_options_t, Bool)

Enables TCP Fast Open on a connection.

func nw_tcp_options_set_enable_keepalive(nw_protocol_options_t, Bool)

Enables TCP keepalives.

func nw_tcp_options_set_keepalive_count(nw_protocol_options_t, UInt32)

Sets the number of keepalive probes that TCP sends before terminating the connection.

func nw_tcp_options_set_keepalive_idle_time(nw_protocol_options_t, UInt32)

Sets the number of seconds of idleness that TCP waits before sending keepalive probes.

func nw_tcp_options_set_keepalive_interval(nw_protocol_options_t, UInt32)

Sets the number of seconds that TCP waits between sending keepalive probes.

func nw_tcp_options_set_maximum_segment_size(nw_protocol_options_t, UInt32)

Sets TCP’s maximum segment size in bytes.

func nw_tcp_options_set_multipath_force_version(nw_protocol_options_t, nw_multipath_version_t)

func nw_tcp_options_set_no_delay(nw_protocol_options_t, Bool)

Disables Nagle’s algorithm for TCP.

func nw_tcp_options_set_no_options(nw_protocol_options_t, Bool)

Sets TCP into no-options mode.

func nw_tcp_options_set_no_push(nw_protocol_options_t, Bool)

Sets TCP into no-push mode.

func nw_tcp_options_set_persist_timeout(nw_protocol_options_t, UInt32)

Sets the TCP persist timeout in seconds, as defined by RFC 6429.

func nw_tcp_options_set_retransmit_connection_drop_time(nw_protocol_options_t, UInt32)

Sets the number of seconds that TCP waits between retransmission attempts.

func nw_tcp_options_set_retransmit_fin_drop(nw_protocol_options_t, Bool)

Causes TCP to drop its connection after not receiving an ACK after a FIN.

func nw_tls_copy_sec_protocol_metadata(nw_protocol_metadata_t) -> sec_protocol_metadata_t

Accesses the result of the TLS handshake.

func nw_tls_copy_sec_protocol_options(nw_protocol_options_t) -> sec_protocol_options_t

Accesses the handshake security options TLS will use.

func nw_tls_create_options() -> nw_protocol_options_t

Initializes a default set of TLS connection options.

func nw_txt_record_access_bytes(nw_txt_record_t, nw_txt_record_access_bytes_t) -> Bool

Accesses the raw bytes contained within a TXT record.

func nw_txt_record_access_key(nw_txt_record_t, UnsafePointer&lt;CChar>, nw_txt_record_access_key_t) -> Bool

Accesses the value for a specific key in a TXT record dictionary.

func nw_txt_record_apply(nw_txt_record_t, nw_txt_record_applier_t) -> Bool

Iterates through all keys in a TXT record dictionary.

func nw_txt_record_copy(nw_txt_record_t?) -> nw_txt_record_t?

Performs a deep copy of a TXT record.

func nw_txt_record_create_dictionary() -> nw_txt_record_t

Initializes a TXT record as a dictionary of strings.

func nw_txt_record_create_with_bytes(UnsafePointer&lt;UInt8>, Int) -> nw_txt_record_t

Initializes a TXT record with raw bytes.

func nw_txt_record_find_key(nw_txt_record_t, UnsafePointer&lt;CChar>) -> nw_txt_record_find_key_t

Checks the status of value associated with a key in a TXT record dictionary.

func nw_txt_record_get_key_count(nw_txt_record_t?) -> Int

Accesses the number of keys stored in the TXT record dictionary.

func nw_txt_record_is_dictionary(nw_txt_record_t) -> Bool

Checks whether a TXT record conforms to a dictionary format.

func nw_txt_record_is_equal(nw_txt_record_t?, nw_txt_record_t?) -> Bool

Checks whether two TXT records are equivalent.

func nw_txt_record_remove_key(nw_txt_record_t, UnsafePointer&lt;CChar>) -> Bool

Removes a data value in a TXT record dictionary.

func nw_txt_record_set_key(nw_txt_record_t, UnsafePointer&lt;CChar>, UnsafePointer&lt;UInt8>?, Int) -> Bool

Sets a data value in a TXT record dictionary.

func nw_udp_create_metadata() -> nw_protocol_metadata_t

Initializes a default UDP message.

func nw_udp_create_options() -> nw_protocol_options_t

Initializes a default set of UDP connection options.

func nw_udp_options_set_prefer_no_checksum(nw_protocol_options_t, Bool)

Configures the connection to not send UDP checksums.

func nw_ws_create_metadata(nw_ws_opcode_t) -> nw_protocol_metadata_t

Initializes a WebSocket message with a specific type code.

func nw_ws_create_options(nw_ws_version_t) -> nw_protocol_options_t

Initializes a default set of WebSocket connection options.

func nw_ws_metadata_copy_server_response(nw_protocol_metadata_t) -> nw_ws_response_t

Accesses the WebSocket server’s response sent during the handshake.

func nw_ws_metadata_get_close_code(nw_protocol_metadata_t) -> nw_ws_close_code_t

Accesses the close code on a WebSocket message.

func nw_ws_metadata_get_opcode(nw_protocol_metadata_t) -> nw_ws_opcode_t

Checks the type code on a WebSocket message.

func nw_ws_metadata_set_close_code(nw_protocol_metadata_t, nw_ws_close_code_t)

Sets a close code on a WebSocket message.

func nw_ws_metadata_set_pong_handler(nw_protocol_metadata_t, dispatch_queue_t, nw_ws_pong_handler_t)

Sets a handler on a Ping message to be invoked when the corresponding Pong message is received.

func nw_ws_options_add_additional_header(nw_protocol_options_t, UnsafePointer&lt;CChar>, UnsafePointer&lt;CChar>)

Adds additional HTTP header fields to be sent by the client during the WebSocket handshake.

func nw_ws_options_add_subprotocol(nw_protocol_options_t, UnsafePointer&lt;CChar>)

Adds to the list of supported application protocols that will be presented to a WebSocket server during connection establishment.

func nw_ws_options_set_auto_reply_ping(nw_protocol_options_t, Bool)

Configures the connection to automatically reply to Ping messages instead of delivering them to you.

func nw_ws_options_set_client_request_handler(nw_protocol_options_t, dispatch_queue_t, nw_ws_client_request_handler_t)

Sets a handler to react to as a server to inbound WebSocket client handshakes.

func nw_ws_options_set_maximum_message_size(nw_protocol_options_t, Int)

Sets the maximum allowed message size, in bytes, to be received by the WebSocket connection.

func nw_ws_options_set_skip_handshake(nw_protocol_options_t, Bool)

Specifies whether the WebSocket protocol skips its handshake and begins framing data once the underlying connection is established.

func nw_ws_request_enumerate_additional_headers(nw_ws_request_t, (UnsafePointer&lt;CChar>, UnsafePointer&lt;CChar>) -> Bool) -> Bool

Enumerates additional HTTP headers in a WebSocket message.

func nw_ws_request_enumerate_subprotocols(nw_ws_request_t, (UnsafePointer&lt;CChar>) -> Bool) -> Bool

Enumerates the supported subprotocols in a WebSocket message.

func nw_ws_response_add_additional_header(nw_ws_response_t, UnsafePointer&lt;CChar>, UnsafePointer&lt;CChar>)

Adds an additional HTTP header to a WebSocket server response.

func nw_ws_response_create(nw_ws_response_status_t, UnsafePointer&lt;CChar>?) -> nw_ws_response_t

Initializes a WebSocket server response with a status and selected subprotocol.

func nw_ws_response_enumerate_additional_headers(nw_ws_response_t, (UnsafePointer&lt;CChar>, UnsafePointer&lt;CChar>) -> Bool) -> Bool

Enumerates the additional HTTP headers in a WebSocket server response.

func nw_ws_response_get_selected_subprotocol(nw_ws_response_t) -> UnsafePointer&lt;CChar>?

Accesses the selected subprotocol in a WebSocket server response.

func nw_ws_response_get_status(nw_ws_response_t?) -> nw_ws_response_status_t

Accesses the status of a WebSocket server response.

## See Also

### Reference

Network Constants

Access Network framework constants used in C.

Network Data Types

