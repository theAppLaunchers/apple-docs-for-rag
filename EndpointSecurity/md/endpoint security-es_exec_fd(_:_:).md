

- Endpoint Security
-  es_exec_fd(\_:\_:) 

Function

# es_exec_fd(\_:\_:)

Gets the file descriptor at the specified position from a process execution event.

macOS 11.0+

``` source
func es_exec_fd(
    _ event: UnsafePointer,
    _ index: UInt32
) -> UnsafePointer
```

## Parameters 

`event`  

The process execution event.

`index`  

The zero-based index of the argument to return. Attempting to read an out-of-bounds index — where `index >= es_fd_arg_count()` — results in undefined behavior.

## Return Value

A pointer to an es_fd_t instance that describes the file descriptor.

## Discussion

This function doesn’t allocate memory for the returned file descriptor description; it points to an es_fd_t inside of `event`. Because you don’t own this memory, don’t try to free it.

Warning

The returned pointer must not outlive the `event` parameter passed to the function, because the pointer will likely be invalid after the function returns.

## See Also

### Process Event Helper Functions

func es_exec_arg(UnsafePointer&lt;es_event_exec_t>, UInt32) -> es_string_token_t

Gets the argument at the specified position from a process execution event.

func es_exec_arg_count(UnsafePointer&lt;es_event_exec_t>) -> UInt32

Gets the number of arguments from a process execution event.

func es_exec_env(UnsafePointer&lt;es_event_exec_t>, UInt32) -> es_string_token_t

Gets the environment variable at the specified position from a process execution event.

func es_exec_env_count(UnsafePointer&lt;es_event_exec_t>) -> UInt32

Gets the number of environment variables from a process execution event.

func es_exec_fd_count(UnsafePointer&lt;es_event_exec_t>) -> UInt32

Gets the number of file descriptors from a process execution event.

struct es_fd_t

A structure that describes an open file descriptor.

