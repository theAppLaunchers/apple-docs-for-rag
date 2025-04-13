

- Kernel
- Kernel Data Types
-  iff_output_func 

Type Alias

# iff_output_func

macOS 10.4+

``` source
typedef errno_t (*iff_output_func)(void *cookie, ifnet_t interface, protocol_family_t protocol, mbuf_t *data);
```

## Parameters 

`cookie`  

The cookie specified when this filter was attached.

`interface`  

The interface the packet is being transmitted on.

`data`  

The fully formed outbound packet in a chain of mbufs. The frame header is already included. The filter function may modify the packet or return a different mbuf chain.

## Return Value

Return: 0 - The caller will continue with normal processing of the packet. EJUSTRETURN - The caller will stop processing the packet, the packet will not be freed. Anything Else - The caller will free the packet and stop processing.

## Discussion

iff_output_func is used to filter fully formed outbound packets. The interface is only valid for the duration of the filter call. If you need to keep a reference to the interface, be sure to call ifnet_reference and ifnet_release.

