

- Security
-  sec_protocol_options_set_key_update_block(\_:\_:\_:) 

Function

# sec_protocol_options_set_key_update_block(\_:\_:\_:)

iOS 12.0+iPadOS 12.0+Mac Catalyst 13.1+macOS 10.14+tvOS 12.0+visionOS 1.0+watchOS 5.0+

``` source
func sec_protocol_options_set_key_update_block(
    _ options: sec_protocol_options_t,
    _ key_update_block: @escaping sec_protocol_key_update_t,
    _ key_update_queue: dispatch_queue_t
)
```

## Parameters 

`options`  

A `sec_protocol_options_t` instance.

`key_update_block`  

A `sec_protocol_key_update_t` block.

## Discussion

```
  Set the key update block.
```

```
  A `dispatch_queue_t` on which the key update block should be called.
```

