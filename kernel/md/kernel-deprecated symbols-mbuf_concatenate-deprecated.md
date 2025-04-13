

- Kernel
- Deprecated Symbols
-  mbuf_concatenate Deprecated

Function

# mbuf_concatenate

macOS 10.4–10.15.4Deprecated

``` source
mbuf_t mbuf_concatenate(mbuf_t dst, mbuf_t src);
```

## Parameters 

`dst`  

The destination mbuf chain.

`src`  

The source mbuf chain.

## Return Value

A pointer to the head of the concatenated mbuf chain. This should be treated as the updated destination mbuf chain; the caller must no longer refer to the original src or dst mbuf chain. Otherwise it returns NULL if the original dst mbuf chain is NULL.

## Discussion

Concatenate mbuf chain src to dst using m_next and return a chain which represents the concatenated chain. The routine does not prevent two chains of different mbuf types to be concatenated, nor does it modify any packet header in the destination chain. Therefore, it's the responsibility of the caller to ensure that the resulted concatenated mbuf chain is correct for further usages.

