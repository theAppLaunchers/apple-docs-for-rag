

- XPC
-  XPC_TYPE_ENDPOINT 

Global Variable

# XPC_TYPE_ENDPOINT

A type that represents a connection in serialized form.

iOS 8.0+iPadOS 8.0+Mac CatalystmacOS 10.10+tvOS 9.0+watchOS 2.0+

``` source
var XPC_TYPE_ENDPOINT: xpc_type_t { get }
```

## Discussion

Unlike a connection, an endpoint is an inert object that doesn’t have any associated runtime activity. So, it is safe to pass an endpoint in a message. Upon receiving an endpoint, the recipient can use xpc_connection_create_from_endpoint(_:) to create as many distinct connections as necessary.

## See Also

### Types of objects

var XPC_TYPE_ACTIVITY: xpc_type_t

A type that represents the XPC activity object.

var XPC_TYPE_ARRAY: xpc_type_t

A type that represents an array of XPC objects.

var XPC_TYPE_BOOL: xpc_type_t

A type that represents a Boolean value.

var XPC_TYPE_CONNECTION: xpc_type_t

A type that represents a connection to a named service.

var XPC_TYPE_DATA: xpc_type_t

A type that represents an arbitrary buffer of bytes.

var XPC_TYPE_DATE: xpc_type_t

A type that represents a date interval.

var XPC_TYPE_DICTIONARY: xpc_type_t

A type that represents a dictionary of XPC objects keyed off of C-strings.

var XPC_TYPE_DOUBLE: xpc_type_t

A type that represents an IEEE-compliant, double-precision floating point value.

var XPC_TYPE_FD: xpc_type_t

A type that represents a POSIX file descriptor.

var XPC_TYPE_INT64: xpc_type_t

A type that represents a signed, 64-bit integer value.

var XPC_TYPE_NULL: xpc_type_t

A type that represents a null object.

var XPC_TYPE_SHMEM: xpc_type_t

A type that represents a region of shared memory.

var XPC_TYPE_STRING: xpc_type_t

A type that represents a null-terminated C-string.

var XPC_TYPE_UINT64: xpc_type_t

A type that represents an unsigned, 64-bit integer value.

var XPC_TYPE_UUID: xpc_type_t

A type that represents a universally unique identifier.

