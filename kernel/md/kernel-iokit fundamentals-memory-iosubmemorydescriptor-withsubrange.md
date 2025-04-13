

- Kernel
- IOKit Fundamentals
- Memory
- IOSubMemoryDescriptor
-  withSubRange 

# withSubRange

Create an IOMemoryDescriptor to describe a subrange of an existing descriptor.

``` source
static IOSubMemoryDescriptor * withSubRange(
 IOMemoryDescriptor *of, 
 IOByteCountoffset, 
 IOByteCountlength, 
 IOOptionBitsoptions); 
```

## Parameters 

`of`  

The parent IOMemoryDescriptor of which a subrange is to be used for the new descriptor, which will be retained by the subrange IOMemoryDescriptor.

`offset`  

A byte offset into the parent memory descriptor's memory.

`length`  

The length of the subrange.

`options`  

kIOMemoryDirectionMask (options:direction) This nibble indicates the I/O direction to be associated with the descriptor, which may affect the operation of the prepare and complete methods on some architectures.

## Return Value

The created IOMemoryDescriptor on success, to be released by the caller, or zero on failure.

## Overview

This method creates and initializes an IOMemoryDescriptor for memory consisting of a subrange of the specified memory descriptor. The parent memory descriptor is retained by the new descriptor.

