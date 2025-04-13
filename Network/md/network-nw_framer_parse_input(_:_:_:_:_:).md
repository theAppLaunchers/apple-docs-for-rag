

- Network
-  nw_framer_parse_input(\_:\_:\_:\_:\_:) 

Function

# nw_framer_parse_input(\_:\_:\_:\_:\_:)

Examines the content of input data while inside your input handler block.

iOS 13.0+iPadOS 13.0+Mac Catalyst 13.1+macOS 10.15+tvOS 13.0+visionOS 1.0+watchOS 6.0+

``` source
func nw_framer_parse_input(
    _ framer: nw_framer_t,
    _ minimum_incomplete_length: Int,
    _ maximum_length: Int,
    _ temp_buffer: UnsafeMutablePointer?,
    _ parse: (UnsafeMutablePointer?, Int, Bool) -> Int
) -> Bool
```

## Parameters 

`framer`  

A network framer instance.

`minimum_incomplete_length`  

The minimum number of bytes that should be delivered to the parse completion.

`maximum_length`  

The maximum number of bytes that should be delivered to the parse completion.

`temp_buffer`  

An optional buffer into which the parser will copy bytes. Use this if you need to make guarantees about byte alignment.

`parse`  

A completion handler that will be called inline to examine a region of bytes.

## Return Value

Returns true if the requested length was available to parse, or false if the conditions could not be met.

## See Also

### Handling Input Data

func nw_framer_set_input_handler(nw_framer_t, nw_framer_input_handler_t)

Sets a block to handle new inbound data.

typealias nw_framer_input_handler_t

A handler that notifies your protocol that new inbound data is available to parse.

typealias nw_framer_parse_completion_t

A handler that examines a range of data being sent or received.

func nw_framer_deliver_input(nw_framer_t, UnsafePointer&lt;UInt8>, Int, nw_framer_message_t, Bool)

Delivers an inbound message containing arbitrary data from your protocol to the application.

func nw_framer_deliver_input_no_copy(nw_framer_t, Int, nw_framer_message_t, Bool) -> Bool

Delivers an inbound message containing a specific number of next received bytes.

func nw_framer_pass_through_input(nw_framer_t)

Indicates that your protocol no longer needs to handle input data.

