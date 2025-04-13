

- Kernel
- Deprecated Symbols
-  mbuf_data_to_physical Deprecated

Function

# mbuf_data_to_physical

macOS 10.4–10.15.4Deprecated

``` source
addr64_t mbuf_data_to_physical(void *ptr);
```

## Parameters 

`ptr`  

A pointer to data stored in an mbuf.

## Return Value

The 64 bit physical address of the mbuf data or NULL if ptr does not point to data stored in an mbuf.

## Discussion

mbuf_data_to_physical is a replacement for mcl_to_paddr. Given a pointer returned from mbuf_data of mbuf_datastart, mbuf_data_to_physical will return the phyical address for that block of data. Note that even though the data is in virtually contiguous span, the underlying physical pages might not be physically contiguous. Because of this, callers must ensure to call this routine for each page boundary. Device drivers that deal with DMA are strongly encouraged to utilize the IOMbufNaturalMemoryCursor and walk down the list of vectors instead of using this interface to obtain the physical address. Use of this routine is therefore discouraged.

