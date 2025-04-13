

- Kernel
- Kernel Data Types
-  sock_upcall 

Type Alias

# sock_upcall

macOS 10.4+

``` source
typedef void (*sock_upcall)(socket_t so, void *cookie, int waitf);
```

## Parameters 

`so`  

A reference to the socket that's ready.

`cookie`  

The cookie passed in when the socket was created.

`waitf`  

Indicates whether or not it's safe to block.

## Discussion

sock_upcall is used by a socket to notify an in kernel client that data is waiting. Instead of making blocking calls in the kernel, a client can specify an upcall which will be called when data is available or the socket is ready for sending.

Calls to your upcall function are not serialized and may be called concurrently from multiple threads in the kernel.

Your upcall function will be called: when there is data more than the low water mark for reading, or when there is space for a write, or when there is a connection to accept, or when a socket is connected, or when a socket is closed or disconnected

