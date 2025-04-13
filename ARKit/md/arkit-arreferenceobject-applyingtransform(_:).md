

- ARKit
- ARReferenceObject
-  applyingTransform(\_:) 

Instance Method

# applyingTransform(\_:)

Returns a new reference object created by applying the specified transform to this reference object’s geometric data.

iOS 12.0+iPadOS 12.0+Mac Catalyst 13.1+

``` source
func applyingTransform(_ transform: simd_float4x4) -> ARReferenceObject
```

## Parameters 

`transform`  

A transform matrix in the local coordinate space of the reference object.

## Return Value

The transformed reference object.

## Discussion

You define the local coordinate space of a reference object when you extract it from an ARWorldMap. If an existing reference object has a local coordinate origin that doesn’t fit well with the object’s intended use, call this method to change the reference object’s origin with respect to the physical object it represents.

When ARKit detects a reference object, the transform of the resulting ARObjectAnchor is based on the orgin of the reference object’s coordinate system. For example, if a reference object represents a physical item that sits on a horizontal surface, virtual content should appear to sit on whatever surface the physical object does. As such, it’s typically useful to align a reference object’s coordinate origin with the bottom of the physical object.

## See Also

### Creating Derivative Reference Objects

func merging(ARReferenceObject) throws -> ARReferenceObject

Returns a new reference object that combines spatial information from both this reference object and another.

