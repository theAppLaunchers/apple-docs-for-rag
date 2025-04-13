

- Kernel
- net
-  inet_arp_init_ifaddr 

Function

# inet_arp_init_ifaddr

macOS 10.4+

``` source
void inet_arp_init_ifaddr(ifnet_t interface, ifaddr_t ipaddr);
```

## Parameters 

`interface`  

The interface the packet was received on.

`ipaddr`  

The ip interface address.

## Discussion

This function should be called in two places, when an IP address is added and when the hardware address changes. This function will setup the ifaddr_t for use with the IP ARP functions. This function will also trigger the transmission of a gratuitous ARP packet.

When the SIOCSIFADDR ioctl is handled, the data parameter will be an ifaddr_t. If this is an IP address, inet_arp_init_ifaddr should be called. This is usually performed in the protocol attachment's ioctl handler.

When the event handler for the protocol attachment receives a KEV_DL_LINK_ADDRESS_CHANGED event, the event handler should call inet_arp_init_ifaddr for each interface ip address.

For an example, see bsd/net/ether_inet_pr_module.c in xnu. Search for inet_arp_init_ifaddr.

## See Also

### Address Resolution

inet_arp_handle_input

inet_arp_lookup

