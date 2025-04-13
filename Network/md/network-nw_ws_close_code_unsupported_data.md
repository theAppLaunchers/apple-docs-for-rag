

- Network
-  nw_ws_close_code_unsupported_data 

Global Variable

# nw_ws_close_code_unsupported_data

An endpoint is terminating the connection because it received a type of data it cannot accept.

iOS 12.0+iPadOS 12.0+Mac Catalyst 13.0+macOS 10.14+tvOS 12.0+visionOS 1.0+watchOS 6.0+

``` source
var nw_ws_close_code_unsupported_data: nw_ws_close_code_t { get }
```

## See Also

### Defined Close Codes

var nw_ws_close_code_normal_closure: nw_ws_close_code_t

A normal closure occurred with no errors.

var nw_ws_close_code_going_away: nw_ws_close_code_t

An endpoint is no longer available, such as when a server is down.

var nw_ws_close_code_protocol_error: nw_ws_close_code_t

An endpoint is terminating the connection due to a protocol error.

var nw_ws_close_code_no_status_received: nw_ws_close_code_t

This value is reserved for local errors and indicates that no Close code was received.

var nw_ws_close_code_abnormal_closure: nw_ws_close_code_t

This value is reserved for local errors and indicates that no Close message was received.

var nw_ws_close_code_invalid_frame_payload_data: nw_ws_close_code_t

An endpoint is terminating the connection because it received data within a message that was inconsistent with the message type.

var nw_ws_close_code_policy_violation: nw_ws_close_code_t

An endpoint is terminating the connection because it received a message that violates its policy.

var nw_ws_close_code_message_too_big: nw_ws_close_code_t

An endpoint is terminating the connection because it received a message that is too big for it to process.

var nw_ws_close_code_mandatory_extension: nw_ws_close_code_t

The WebSocket client expected the server to negotiate one or more extensions that were not negotiated.

var nw_ws_close_code_internal_server_error: nw_ws_close_code_t

The server is terminating the connection because it encountered an unexpected condition that prevented it from fulfilling the request.

var nw_ws_close_code_tls_handshake: nw_ws_close_code_t

This value is reserved for local errors and indicates that the TLS handshake failed.

