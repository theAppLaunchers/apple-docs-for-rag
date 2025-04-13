

- Kernel
- IOKit Fundamentals
- Memory
- IODMACommand
-  prepareWithSpecification 

Instance Method

# prepareWithSpecification

Prepare the memory for an I/O transfer with a new specification.

macOS 10.15.2+

``` source
virtual IOReturn prepareWithSpecification(SegmentFunction outSegFunc, const SegmentOptions *segmentOptions, uint32_t mappingOptions, IOMapper *mapper, uint64_t offset, uint64_t length, bool flushCache, bool synchronize);
```

## Parameters 

`outSegFunc`  

SegmentFunction to call to output one physical segment. A set of nine commonly required segment functions are provided.

`segmentOptions`  

A structure with the segment configuration options.

`mappingOptions`  

is the type of mapping that is required to translate an IOMemoryDescriptor into the desired number of bits. For instance if your hardware only supports 32 bits but must run on machines with \> 4G of RAM some mapping will be required. Number of bits will be specified in numAddressBits, see below.This parameter can take 3 values:- kNonCoherent - used for non-coherent hardware transfers, Mapped - Validate that all I/O bus generated addresses are within the number of addressing bits specified, Bypassed indicates that bypassed addressing is required, this is used when the hardware transferes are into coherent memory but no mapping is required. See also prepare() for failure cases.

`mapper`  

For mapping types kMapped & kBypassed mapper is used to define the hardware that will perform the mapping, defaults to the system mapper.

`offset`  

defines the starting offset in the memory descriptor the DMA command will operate on. genIOVMSegments will produce its results based on the offset and length passed to the prepare method.

`length`  

defines the ending position in the memory descriptor the DMA command will operate on. genIOVMSegments will produce its results based on the offset and length passed to the prepare method.

`flushCache`  

Flush the caches for the memory descriptor and make certain that the memory cycles are complete. Defaults to true for kNonCoherent and is ignored by the other types.

`synchronize`  

Copy any buffered data back from the target IOMemoryDescriptor. Defaults to true, if synchronize() is being used to explicitly copy data, passing false may avoid an unneeded copy.

## Return Value

An IOReturn code. Can fail if the mapping type is not recognised, if one of the 3 mandatory parameters are set to 0, if a 32 bit output function is selected when more than 32 bits of address is required or, if kBypassed is requested on a machine that doesn't support bypassing.

## Discussion

Allocate the mapping resources neccessary for this transfer, specifying a sub range of the IOMemoryDescriptor that will be the target of the I/O. The complete() method frees these resources. Data may be copied to buffers for kIODirectionOut memory descriptors, depending on hardware mapping resource availabilty or alignment restrictions. It should be noted that the this function may block and should only be called on the clients context, i.e never call this routine while gated; also the call itself is not thread safe though this should be an issue as each IODMACommand is independant.

## See Also

### Preparing the Transfer Operation

prepare

Prepare the memory for an I/O transfer.

- prepare

Prepare the memory for an I/O transfer.

prepareWithSpecification

Prepare the memory for an I/O transfer with a new specification.

- prepareWithSpecification

Prepare the memory for an I/O transfer with a new specification.

complete

Complete processing of DMA mappings after an I/O transfer is finished.

- complete

Complete processing of DMA mappings after an I/O transfer is finished.

synchronize

Bring IOMemoryDescriptor and IODMACommand buffers into sync.

- synchronize

Bring IOMemoryDescriptor and IODMACommand buffers into sync.

