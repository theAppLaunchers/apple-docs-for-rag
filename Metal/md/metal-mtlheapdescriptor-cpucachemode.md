

- Metal
- MTLHeapDescriptor
-  cpuCacheMode 

Instance Property

# cpuCacheMode

The CPU cache behavior for any resources you allocate from the heaps you create with this descriptor.

iOS 10.0+iPadOS 10.0+Mac Catalyst 13.1+macOS 10.13+tvOS 10.0+visionOS 1.0+

``` source
var cpuCacheMode: MTLCPUCacheMode { get set }
```

## Discussion

This property’s default value is MTLCPUCacheMode.defaultCache.

The resources you allocate from a heap inherit that heap’s CPU cache mode.

## See Also

### Configuring a Heap

var type: MTLHeapType

The memory placement strategy for any resources you allocate from the heaps you create with this descriptor.

var storageMode: MTLStorageMode

The storage mode for the heaps you create with this descriptor.

var hazardTrackingMode: MTLHazardTrackingMode

The hazard tracking behavior for any resources you allocate from the heaps you create with this descriptor.

var resourceOptions: MTLResourceOptions

The combined behavior for any resources you allocate from the heaps you create with this descriptor.

var size: Int

The total amount of memory, in bytes, for the heaps you create with this descriptor.

var sparsePageSize: MTLSparsePageSize

The page size for any resources you allocate from the heaps you create with this descriptor.

