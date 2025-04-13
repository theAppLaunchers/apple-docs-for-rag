

- Security
-  sec_protocol_options_add_tls_application_protocol(\_:\_:) 

Function

# sec_protocol_options_add_tls_application_protocol(\_:\_:)

iOS 12.0+iPadOS 12.0+Mac Catalyst 13.1+macOS 10.14+tvOS 12.0+visionOS 1.0+watchOS 5.0+

``` source
func sec_protocol_options_add_tls_application_protocol(
    _ options: sec_protocol_options_t,
    _ application_protocol: UnsafePointer
)
```

## Parameters 

`options`  

A `sec_protocol_options_t` instance.

`application_protocol`  

A NULL-terminated string defining the application protocol.

## Discussion

```
  Add an application protocol supported by clients of this protocol instance.
```

