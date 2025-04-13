

- ARKit
- ARSession
-  createReferenceObject(transform:center:extent:completionHandler:) 

Instance Method

# createReferenceObject(transform:center:extent:completionHandler:)

Creates a reference object (for 3D object detection) from the specified region of the session’s world space.

iOS 12.0+iPadOS 12.0+Mac Catalyst 13.1+

``` source
func createReferenceObject(
    transform: simd_float4x4,
    center: simd_float3,
    extent: simd_float3,
    completionHandler: @escaping (ARReferenceObject?, (any Error)?) -> Void
)
```

``` source
func createReferenceObject(
    transform: simd_float4x4,
    center: simd_float3,
    extent: simd_float3
) async throws -> ARReferenceObject
```

## Parameters 

`transform`  

A transform matrix defining the origin and orientation of the local coordinate system for the region to extract.

`center`  

A point, relative to the origin specified by `transform`, that defines the center of the bounding box for the region to extract.

`extent`  

The width, height, and depth of the region to extract, centered on the `center` point and oriented to the local coordinate system specified by `transform`.

`completionHandler`  

A handler to be invoked asynchronously after ARKit finishes creating the reference object. The handler takes two parameters:

referenceObject  
A ARReferenceObject that represents the specified region of the world map, or `nil` if a reference object could not be created.

error  
If the `referenceObject` is `nil`, an ARError describing the failure.

## Discussion

Important

This method is valid only when running a session with ARObjectScanningConfiguration, which enables the high-fidelity spatial data collection needed for scanning reference objects. Calling this method on a session with a different configuration immediately invokes your `completionHandler` with an error.

To use the extracted reference object for 3D object detection, assign it to the detectionObjects property of a world tracking configuration. You can bundle reference objects in an app by saving them to files and adding them to an Xcode asset catalog.

When ARKit detects a reference image, the transform of the resulting ARObjectAnchor is based on the orgin of the reference object’s coordinate system—the transform you specify when extracting the reference object. For example, if a reference object represents a physical item that sits on a horizontal surface, virtual content should appear to sit on whatever surface the physical object does. To adjust a reference object’s origin after extracting it, use the applyingTransform(_:) method.

