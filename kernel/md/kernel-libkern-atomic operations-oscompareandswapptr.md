

- Kernel
- libkern
- Atomic Operations
-  OSCompareAndSwapPtr 

Function

# OSCompareAndSwapPtr

Compare and swap operation, performed atomically with respect to all devices that participate in the coherency architecture of the platform.

macOS 10.6+

``` source
Boolean OSCompareAndSwapPtr(void *oldValue, void *newValue, void *volatile *address);
```

## Parameters 

`oldValue`  

The pointer value to compare at address.

`newValue`  

The pointer value to write to address if oldValue compares true.

`address`  

The pointer-size aligned address of the data to update atomically.

## Return Value

true if newValue was written to the address.

## Discussion

The OSCompareAndSwapPtr function compares the pointer-sized value at the specified address with oldVal. The value of newValue is written to the address only if oldValue and the value at the address are equal. OSCompareAndSwapPtr returns true if newValue is written to the address; otherwise, it returns false.

This function guarantees atomicity only with main system memory. It is specifically unsuitable for use on noncacheable memory such as that in devices; this function cannot guarantee atomicity, for example, on memory mapped from a PCI device. Additionally, this function incorporates a memory barrier on systems with weakly-ordered memory architectures.

## See Also

### Compare and Swap

OSCompareAndSwap

Compare and swap operation, performed atomically with respect to all devices that participate in the coherency architecture of the platform.

OSCompareAndSwap64

64-bit compare and swap operation.

