

- Kernel
- Deprecated Symbols
-  mbuf_set_vlan_tag Deprecated

Function

# mbuf_set_vlan_tag

macOS 10.4–10.15.4Deprecated

``` source
errno_t mbuf_set_vlan_tag(mbuf_t mbuf, u_int16_t vlan);
```

## Parameters 

`mbuf`  

The mbuf containing the packet.

`vlan`  

The protocol family of the aux data to add.

## Return Value

0 upon success otherwise the errno error.

## Discussion

This function is used by interfaces that support vlan tagging in hardware. This function will set properties in the mbuf to indicate which vlan the packet was received for.

