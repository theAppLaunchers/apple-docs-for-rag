

- Network
-  nw_connection_send(\_:\_:\_:\_:\_:) 

Function

# nw_connection_send(\_:\_:\_:\_:\_:)

Sends data on a connection.

iOS 12.0+iPadOS 12.0+Mac Catalyst 13.1+macOS 10.14+tvOS 12.0+visionOS 1.0+watchOS 5.0+

``` source
func nw_connection_send(
    _ connection: nw_connection_t,
    _ content: dispatch_data_t?,
    _ context: nw_content_context_t,
    _ is_complete: Bool,
    _ completion: @escaping nw_connection_send_completion_t
)
```

## Parameters 

`connection`  

A network connection instance.

`content`  

The data to send on the connection. May be nil if this send marks its context as complete, such as by sending `NW_CONNECTION_FINAL_MESSAGE_CONTEXT` as the context and marking the send complete to send a write-close.

`context`  

The context associated with the content, which represents a logical message to be sent on the connection. All content sent within a single context will be sent as an in-order unit, up until the point that the context is marked complete. Once a context is marked complete, it may be re-used as a new logical message. Protocols like TCP that cannot send multiple independent messages at once (serial bytestreams) will only start processing a new context once the prior context has been marked complete. Defaults to `NW_CONNECTION_DEFAULT_MESSAGE_CONTEXT`.

`is_complete`  

A flag indicating if the caller’s sending context (logical message) is now complete. Until a context is marked complete, content sent for other contexts may not be sent immediately (if the protocol requires sending bytes serially, like TCP). For datagram protocols, like UDP, this flag indicates that the content represents a complete datagram.

When sending using streaming protocols like TCP, this flag can be used to mark the end of a single message on the stream, of which there may be many. However, it can also indicate that the connection should send a “write close” (a TCP FIN) if the sending context is the final context on the connection. Specifically, to send a “write close”, pass `NW_CONNECTION_FINAL_MESSAGE_CONTEXT` or `NW_CONNECTION_DEFAULT_STREAM_CONTEXT` for the context (or create a custom context and call nw_content_context_set_is_final(_:_:)), and mark the send as complete.

`completion`  

A completion handler to notify the caller when content has been processed by the connection, or a marker that this data is idempotent (`NW_CONNECTION_SEND_IDEMPOTENT_CONTENT`) and may be sent multiple times as fast open data if nw_parameters_set_fast_open_enabled(_:_:) was called.

## See Also

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

