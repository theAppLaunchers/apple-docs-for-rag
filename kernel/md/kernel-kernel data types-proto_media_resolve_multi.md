

- Kernel
- Kernel Data Types
-  proto_media_resolve_multi 

Type Alias

# proto_media_resolve_multi

macOS 10.4+

``` source
typedef errno_t (*proto_media_resolve_multi)(ifnet_t ifp, const struct sockaddr *proto_addr, struct sockaddr_dl *out_ll, size_t ll_len);
```

## Parameters 

`ifp`  

The interface.

`proto_addr`  

The protocol address.

`out_ll`  

A sockaddr_dl to copy the link layer multicast in to.

`ll_len`  

The length of data allocated for out_ll.

## Return Value

Return zero on success or an errno error value on failure.

## Discussion

proto_media_resolve_multi is called to resolve a protocol layer mulitcast address to a link layer multicast address.

