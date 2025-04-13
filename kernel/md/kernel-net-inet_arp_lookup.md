

- Kernel
- net
-  inet_arp_lookup 

Function

# inet_arp_lookup

macOS 10.4+

``` source
errno_t inet_arp_lookup(ifnet_t interface, const struct sockaddr_in *ip_dest, struct sockaddr_dl *ll_dest, size_t ll_dest_len, route_t hint, mbuf_t packet);
```

## Parameters 

`interface`  

The interface the packet is being sent on.

`ip_dest`  

The ip destination of the packet.

`ll_dest`  

On output, the link-layer destination.

`ll_dest_len`  

The length of the buffer for ll_dest.

`hint`  

Any routing hint passed down from the protocol.

`packet`  

The packet being transmitted.

## Return Value

May return an error such as EHOSTDOWN or ENETUNREACH. If this function returns EJUSTRETURN, the packet has been queued and will be sent when an arp response is received. If any other value is returned, the caller is responsible for disposing of the packet.

## Discussion

This function will check the routing table for a cached arp entry or trigger an arp query to resolve the ip address to a link-layer address.

Arp entries are stored in the routing table. This function will lookup the ip destination in the routing table. If the destination requires forwarding to a gateway, the route of the gateway will be looked up. The route entry is inspected to determine if the link layer destination address is known. If unknown, the arp generation function for IP attached to the interface is called to create an arp request packet.

## See Also

### Address Resolution

inet_arp_handle_input

inet_arp_init_ifaddr

