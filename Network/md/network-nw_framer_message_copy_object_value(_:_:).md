

- Network
-  nw_framer_message_copy_object_value(\_:\_:) 

Function

# nw_framer_message_copy_object_value(\_:\_:)

Accesses an NSObject value stored in a framer message.

iOS 13.0+iPadOS 13.0+Mac Catalyst 13.1+macOS 10.15+tvOS 13.0+visionOS 1.0+watchOS 6.0+

``` source
func nw_framer_message_copy_object_value(
    _ message: nw_framer_message_t,
    _ key: UnsafePointer
) -> Any?
```

## See Also

### Customizing Framer Messages

typealias nw_framer_message_t

A message for a custom protocol, in which you can store arbitrary key-value pairs.

func nw_protocol_metadata_is_framer_message(nw_protocol_metadata_t) -> Bool

Checks if a metadata object represents a custom framer protocol message.

func nw_framer_protocol_create_message(nw_protocol_definition_t) -> nw_framer_message_t

Initializes an empty message for a custom framer definition.

func nw_framer_message_create(nw_framer_t) -> nw_framer_message_t

Initializes an empty message from within a framer implementation.

func nw_framer_message_set_value(nw_framer_message_t, UnsafePointer&lt;CChar>, UnsafeMutableRawPointer?, nw_framer_message_dispose_value_t?)

Sets a value to be stored in a framer message, with a completion to call to disposed the stored value when the message is released.

typealias nw_framer_message_dispose_value_t

A handler that’s invoked when your custom value needs to be released due to a message being released or the value being replaced.

func nw_framer_message_set_object_value(nw_framer_message_t, UnsafePointer&lt;CChar>, Any?)

Sets an NSObject value to be stored in a framer message.

func nw_framer_message_access_value(nw_framer_message_t, UnsafePointer&lt;CChar>, (UnsafeRawPointer?) -> Bool) -> Bool

Accesses a custom value stored in a framer message.

