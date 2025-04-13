

- Kernel
- Kernel Data Types
-  sf_listen_func 

Type Alias

# sf_listen_func

macOS 10.4+

``` source
typedef errno_t (*sf_listen_func)(void *cookie, socket_t so);
```

## Parameters 

`cookie`  

Cookie value specified when the filter attach was called.

`so`  

The socket the filter is attached to.

## Return Value

Return: 0 - The caller will continue with normal processing of listen. EJUSTRETURN - The caller will return with a value of 0 (no error) from that point without further processing the listen command. The protocol will not see the call. Anything Else - The caller will stop processing and return this error.

## Discussion

sf_listen_func is called before performing listen on a socket.

