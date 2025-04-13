

- Metal
- MTLResidencySetDescriptor
-  label 

Instance Property

# label

An optional name that can help you identify a residency set you create with the descriptor.

iOS 18.0+iPadOS 18.0+Mac Catalyst 18.0+macOS 15.0+tvOS 18.0+visionOS 2.0+

``` source
var label: String? { get set }
```

## Discussion

Metal applies the value of this property to the label property of an MTLResidencySet that you create by passing the descriptor to makeResidencySet(descriptor:).

## See Also

### Configuring the Residency Set

var initialCapacity: Int

The number of allocations a new residency set can store without reallocating memory.

