

- Core Foundation
- CFAllocatorContext
-  allocate 

Instance Property

# allocate

A prototype for a function callback that allocates memory of a requested size. In implementing this function, allocate a block of memory of at least `size` bytes and return a pointer to the start of the block. The `hint` argument is a bitfield that you should currently not use (that is, assign 0). The `size` parameter should always be greater than 0. If it is not, or if problems in allocation occur, return `NULL`. This function pointer may not be assigned `NULL`.

iOSiPadOSMac CatalystmacOStvOSvisionOSwatchOS

``` source
var allocate: CFAllocatorAllocateCallBack!
```

