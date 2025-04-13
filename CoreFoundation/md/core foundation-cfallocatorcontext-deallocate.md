

- Core Foundation
- CFAllocatorContext
-  deallocate 

Instance Property

# deallocate

A prototype for a function callback that deallocates a given block of memory. In implementing this function, make the block of memory pointed to by `ptr` available for subsequent reuse by the allocator but unavailable for continued use by the program. The `ptr` parameter cannot be `NULL` and if the `ptr` parameter is not a block of memory that has been previously allocated by the allocator, the results are undefined; abnormal program termination can occur. You can set this callback to `NULL`, in which case the CFAllocatorDeallocate(_:_:) function has no effect.

iOSiPadOSMac CatalystmacOStvOSvisionOSwatchOS

``` source
var deallocate: CFAllocatorDeallocateCallBack!
```

