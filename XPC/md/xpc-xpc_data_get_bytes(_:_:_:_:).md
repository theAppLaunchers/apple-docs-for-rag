

- XPC
-  xpc_data_get_bytes(\_:\_:\_:\_:) 

Function

# xpc_data_get_bytes(\_:\_:\_:\_:)

Copies the bytes in a data object into the specified buffer.

iOS 5.0+iPadOS 5.0+Mac Catalyst 13.1+macOS 10.7+

``` source
func xpc_data_get_bytes(
    _ xdata: xpc_object_t,
    _ buffer: UnsafeMutableRawPointer,
    _ off: Int,
    _ length: Int
) -> Int
```

## Parameters 

`xdata`  

The data object which is to be examined.

`buffer`  

The buffer in which to copy the data object’s bytes.

`off`  

The offset at which to begin the copy. If this offset is greater than the length of the data element, nothing is copied. Pass 0 to start the copy at the beginning of the buffer.

`length`  

The length of the destination buffer.

## Return Value

The number of bytes that were copied into the buffer.

## See Also

### Data objects

func xpc_data_create(UnsafeRawPointer?, Int) -> xpc_object_t

Creates an XPC object that represents a buffer of bytes.

func xpc_data_create_with_dispatch_data(dispatch_data_t) -> xpc_object_t

Creates an XPC object that represents a buffer of bytes that the specified GCD data object describes.

func xpc_data_get_bytes_ptr(xpc_object_t) -> UnsafeRawPointer?

Returns a pointer to the internal storage of a data object.

func xpc_data_get_length(xpc_object_t) -> Int

Returns the length of the data that an XPC data object encapsulates.

