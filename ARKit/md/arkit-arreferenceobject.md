

- ARKit
-  ARReferenceObject 

Class

# ARReferenceObject

The description of a 3D object that you want ARKit to detect in the physical environment.

iOS 12.0+iPadOS 12.0+Mac Catalyst 13.1+

``` source
class ARReferenceObject
```

## Overview

Object detection in ARKit lets you trigger AR content when the session recognizes a known 3D object. For example, your app could detect sculptures in an art museum and provide a virtual curator, or detect tabletop gaming figures and create visual effects for the game.

To provide a known 3D object for detection, you scan a real-world object using ARKit:

1.  Run an AR session using ARObjectScanningConfiguration to enable collection of high-fidelity spatial mapping data.

2.  In that session, point the device camera at the real-world object from various angles, allowing ARKit to build up an internal map of the object and its surroundings. For an example of guiding user interactions to produce good scan data, see Scanning and Detecting 3D Objects.

3.  Determine the portion of the session’s world coordinate space representing the object to be recognized, and call createReferenceObject(transform:center:extent:completionHandler:) to get that portion as an ARReferenceObject ready for use in object detection.

4.  To save the reference object for use later or elsewhere, use the export(to:previewImage:) method to create an `.arobject` file.

To detect objects in an AR session, pass a collection of reference objects to your session configuration’s detectionObjects property. You need not scan and detect objects in the same app: For example, you might create one app for scanning museum collections that outputs `.arobject` files, then bundle those files into another app meant for museum visitors.

To bundle reference objects into an app, use your Xcode project’s asset catalog:

1.  In your asset catalog, use the Add (+) button to create an AR Resource Group.

2.  Drag `.arobject` into the resource group to create AR Reference Object entries in the asset catalog.

3.  Optionally, use the Xcode inspector panel to provide a descriptive name for the object, which appears as the name property at runtime and can be useful for debugging.

## Topics

### Loading Reference Objects

init(archiveURL: URL) throws

Loads a reference object from the specified file URL.

class func referenceObjects(inGroupNamed: String, bundle: Bundle?) -> Set&lt;ARReferenceObject>?

Loads all reference objects in the specified AR Resource Group in your Xcode project’s asset catalog.

### Examining a Reference Object

var name: String?

A descriptive name for the reference object.

var resourceGroupName: String?

var center: simd_float3

The center point of the reference object’s space-mapping data.

var extent: simd_float3

The size of the reference object’s space-mapping data.

var scale: simd_float3

A scale factor for the local coordinate space the reference object defines.

### Saving Recorded Objects

func export(to: URL, previewImage: UIImage?) throws

Writes a binary representation of the object to the specified file URL.

class let archiveExtension: String

The standard filename extension for exported ARReferenceObject instances.

### Creating Derivative Reference Objects

func applyingTransform(simd_float4x4) -> ARReferenceObject

Returns a new reference object created by applying the specified transform to this reference object’s geometric data.

func merging(ARReferenceObject) throws -> ARReferenceObject

Returns a new reference object that combines spatial information from both this reference object and another.

### Debugging a Reference Object

var rawFeaturePoints: ARPointCloud

A coarse representation of the space-mapping data contained in the reference object.

## Relationships

### Inherits From

- NSObject

### Conforms To

- CVarArg
- CustomDebugStringConvertible
- CustomStringConvertible
- Equatable
- Hashable
- NSCoding
- NSObjectProtocol
- NSSecureCoding
- Sendable

## See Also

### Physical Objects

Visualizing and interacting with a reconstructed scene

Estimate the shape of the physical environment using a polygonal mesh.

Scanning and Detecting 3D Objects

Record spatial features of real-world objects, then use the results to find those objects in the user’s environment and trigger AR content.

class ARObjectAnchor

An anchor for a real-world 3D object that ARKit detects in the physical environment.

