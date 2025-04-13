

- ARKit
- ARReferenceObject
-  merging(\_:) 

Instance Method

# merging(\_:)

Returns a new reference object that combines spatial information from both this reference object and another.

iOS 12.0+iPadOS 12.0+Mac Catalyst 13.1+

``` source
func merging(_ object: ARReferenceObject) throws -> ARReferenceObject
```

## Parameters 

`object`  

The other reference object with which to combine this reference object.

## Return Value

A new ARReferenceObject that includes the spatial information from both objects. From Swift, this method throws an ARError if the two objects cannot be merged. From Objective-C, it returns `nil` and populates the `error` parameter with a description of the failure.

## Discussion

The accuracy of 3D object detection depends on similarity of lighting and environmental conditions between when you scan a real object (producing an ARReferenceObject) and when a user of your app attempts to detect that object. If, for example, you scan an object in a bright environment, then a user attempts to detect it in a dark environment, ARKit may fail to recognize that the real object matches the reference object, or may not detect the object quickly.

To make a reference object that is more robust in a wide variety of detection conditions, scan the same real-world object multiple times: For each scan, vary the lighting conditions or the background environment to capture the variety of situations in which your app might attempt to detect the same real object. Then, use this method to combine those scan results into a single ARReferenceObject incorporating recognition information for all the conditions you scanned in.

## See Also

### Creating Derivative Reference Objects

func applyingTransform(simd_float4x4) -> ARReferenceObject

Returns a new reference object created by applying the specified transform to this reference object’s geometric data.

