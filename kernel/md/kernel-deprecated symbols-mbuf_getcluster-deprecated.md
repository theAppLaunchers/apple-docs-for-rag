

- Kernel
- Deprecated Symbols
-  mbuf_getcluster Deprecated

Function

# mbuf_getcluster

macOS 10.4–10.15.4Deprecated

``` source
errno_t mbuf_getcluster(mbuf_how_t how, mbuf_type_t type, size_t size, mbuf_t *mbuf);
```

## Parameters 

`how`  

Blocking or non-blocking.

`type`  

The type of the mbuf.

`size`  

The size of the cluster to be allocated. Supported sizes for a cluster are be 2048, 4096, or 16384. Any other value with return EINVAL. Note that clusters greater than 4096 bytes might not be available in all configurations; the caller must additionally check for ENOTSUP (see below).

`mbuf`  

The mbuf the cluster will be attached to.

## Return Value

0 on success, errno error on failure. If you specified NULL for the mbuf, any intermediate mbuf that may have been allocated will be freed. If you specify an mbuf value in \*mbuf, mbuf_mclget will not free it. EINVAL - Invalid parameter ENOMEM - Not enough memory available ENOTSUP - The caller had requested greater than 4096 bytes cluster and the system is unable to fulfill it due to the lack of jumbo clusters support based on the configuration. In this case, the caller is advised to use 4096 bytes or smaller during subsequent requests.

## Discussion

Allocate a cluster of the requested size and attach it to an mbuf for use as external data. If mbuf points to a NULL mbuf_t, an mbuf will be allocated for you. If mbuf points to a non-NULL mbuf_t, mbuf_getcluster may return a different mbuf_t than the one you passed in.

