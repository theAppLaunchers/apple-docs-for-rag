

- Network
-  nw_advertise_descriptor_t 

Type Alias

# nw_advertise_descriptor_t

A description used to advertise the Bonjour service that a listener provides.

iOS 12.0+iPadOS 12.0+Mac Catalyst 13.0+macOS 10.14+tvOS 12.0+visionOS 1.0+watchOS 6.0+

``` source
typealias nw_advertise_descriptor_t = any OS_nw_advertise_descriptor
```

## Topics

### Advertising Bonjour Services

func nw_advertise_descriptor_create_bonjour_service(UnsafePointer&lt;CChar>?, UnsafePointer&lt;CChar>, UnsafePointer&lt;CChar>?) -> nw_advertise_descriptor_t?

Initializes a Bonjour service to advertise.

func nw_advertise_descriptor_set_no_auto_rename(nw_advertise_descriptor_t, Bool)

Sets a Boolean to indicate whether the service prohibits automatic renaming in the event of a name conflict.

func nw_advertise_descriptor_get_no_auto_rename(nw_advertise_descriptor_t) -> Bool

Checks whether the service prohibits automatic renaming in the event of a name conflict.

### Configuring TXT Records

func nw_advertise_descriptor_set_txt_record(nw_advertise_descriptor_t, UnsafeRawPointer?, Int)

Sets the TXT record as a raw buffer to advertise with the service.

func nw_advertise_descriptor_set_txt_record_object(nw_advertise_descriptor_t, nw_txt_record_t?)

Sets the TXT record to advertise with the service.

func nw_advertise_descriptor_copy_txt_record_object(nw_advertise_descriptor_t) -> nw_txt_record_t?

Accesses the TXT record to advertise with the service.

## See Also

### Data Types

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

