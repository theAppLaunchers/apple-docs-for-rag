

- Kernel
- Kernel Data Types
-  sf_attach_func 

Type Alias

# sf_attach_func

macOS 10.4+

``` source
typedef errno_t (*sf_attach_func)(void **cookie, socket_t so);
```

## Parameters 

`cookie`  

Used to allow the socket filter to set the cookie for this attachment.

`so`  

The socket the filter is being attached to.

## Return Value

If you return a non-zero value, your filter will not be attached to this socket.

## Discussion

sf_attach_func is called to notify the filter it has been attached to a socket. The filter may allocate memory for this attachment and use the cookie to track it. This filter is called in one of two cases:

1.  You've installed a global filter and a new socket was created.

2.  Your non-global socket filter is being attached using the SO_NKE socket option.

