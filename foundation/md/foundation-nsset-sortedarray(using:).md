

- Foundation
- NSSet
-  sortedArray(using:) 

Instance Method

# sortedArray(using:)

Returns an array of the set’s content sorted as specified by a given array of sort descriptors.

iOS 4.0+iPadOS 4.0+Mac Catalyst 13.1+macOS 10.6+tvOS 9.0+visionOS 1.0+watchOS 2.0+

``` source
func sortedArray(using sortDescriptors: [NSSortDescriptor]) -> [Any]
```

## Parameters 

`sortDescriptors`  

An array of NSSortDescriptor objects.

## Return Value

An NSArray containing the set’s content sorted as specified by `sortDescriptors`.

## Discussion

The first descriptor specifies the primary key path to be used in sorting the set’s contents. Any subsequent descriptors are used to further refine sorting of objects with duplicate values. See NSSortDescriptor for additional information.

