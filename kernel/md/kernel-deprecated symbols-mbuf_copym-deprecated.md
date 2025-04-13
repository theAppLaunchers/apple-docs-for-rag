

- Kernel
- Deprecated Symbols
-  mbuf_copym Deprecated

Function

# mbuf_copym

macOS 10.4–10.15.4Deprecated

``` source
errno_t mbuf_copym(const mbuf_t src, size_t offset, size_t len, mbuf_how_t how, mbuf_t *new_mbuf);
```

## Parameters 

`src`  

The source mbuf.

`offset`  

The offset in the mbuf to start copying from.

`len`  

The the number of bytes to copy.

`how`  

To block or not to block, that is a question.

`new_mbuf`  

Upon success, the newly allocated mbuf.

## Return Value

0 upon success otherwise the errno error.

## Discussion

Copies len bytes from offset from src to a new mbuf. If the original mbuf contains a packet header, the new mbuf will contain similar packet header except for any tags which may be associated with the original mbuf. mbuf_dup() should be used instead if tags are to be copied to the new mbuf.

