

- Network
-  nw_txt_record_t 

Type Alias

# nw_txt_record_t

A dictionary representing a TXT record in a DNS packet.

iOS 12.0+iPadOS 12.0+Mac Catalyst 13.0+macOS 10.14+tvOS 12.0+visionOS 1.0+watchOS 6.0+

``` source
typealias nw_txt_record_t = any OS_nw_txt_record
```

## Topics

### Creating TXT Records

func nw_txt_record_create_dictionary() -> nw_txt_record_t

Initializes a TXT record as a dictionary of strings.

func nw_txt_record_create_with_bytes(UnsafePointer&lt;UInt8>, Int) -> nw_txt_record_t

Initializes a TXT record with raw bytes.

func nw_txt_record_copy(nw_txt_record_t?) -> nw_txt_record_t?

Performs a deep copy of a TXT record.

func nw_txt_record_set_key(nw_txt_record_t, UnsafePointer&lt;CChar>, UnsafePointer&lt;UInt8>?, Int) -> Bool

Sets a data value in a TXT record dictionary.

func nw_txt_record_remove_key(nw_txt_record_t, UnsafePointer&lt;CChar>) -> Bool

Removes a data value in a TXT record dictionary.

### Examining TXT Records

func nw_txt_record_is_dictionary(nw_txt_record_t) -> Bool

Checks whether a TXT record conforms to a dictionary format.

func nw_txt_record_get_key_count(nw_txt_record_t?) -> Int

Accesses the number of keys stored in the TXT record dictionary.

func nw_txt_record_apply(nw_txt_record_t, nw_txt_record_applier_t) -> Bool

Iterates through all keys in a TXT record dictionary.

typealias nw_txt_record_applier_t

A block that iterates over values and keys in a TXT record dictionary.

func nw_txt_record_access_key(nw_txt_record_t, UnsafePointer&lt;CChar>, nw_txt_record_access_key_t) -> Bool

Accesses the value for a specific key in a TXT record dictionary.

typealias nw_txt_record_access_key_t

A block that returns a value in a TXT record dictionary.

func nw_txt_record_find_key(nw_txt_record_t, UnsafePointer&lt;CChar>) -> nw_txt_record_find_key_t

Checks the status of value associated with a key in a TXT record dictionary.

struct nw_txt_record_find_key_t

Status values describing what kind of value is stored in a TXT record dictionary.

func nw_txt_record_is_equal(nw_txt_record_t?, nw_txt_record_t?) -> Bool

Checks whether two TXT records are equivalent.

func nw_txt_record_access_bytes(nw_txt_record_t, nw_txt_record_access_bytes_t) -> Bool

Accesses the raw bytes contained within a TXT record.

typealias nw_txt_record_access_bytes_t

A block that provides access to the raw bytes of a TXT record.

## See Also

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

