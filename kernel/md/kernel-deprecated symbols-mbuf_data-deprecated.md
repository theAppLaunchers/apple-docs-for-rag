

- Kernel
- Deprecated Symbols
-  mbuf_data Deprecated

Function

# mbuf_data

macOS 10.4–10.15.4Deprecated

``` source
void * mbuf_data(mbuf_t mbuf);
```

## Parameters 

`mbuf`  

The mbuf.

## Return Value

A pointer to the data in the mbuf.

## Discussion

Returns a pointer to the start of data in this mbuf. There may be additional data on chained mbufs. The data you're looking for may not be virtually contiguous if it spans more than one mbuf. In addition, data that is virtually contiguous might not be represented by physically contiguous pages; see further comments in mbuf_data_to_physical. Use mbuf_len to determine the lenght of data available in this mbuf. If a data structure you want to access stradles two mbufs in a chain, either use mbuf_pullup to get the data contiguous in one mbuf or copy the pieces of data from each mbuf in to a contiguous buffer. Using mbuf_pullup has the advantage of not having to copy the data. On the other hand, if you don't make sure there is space in the mbuf, mbuf_pullup may fail and free the mbuf.

