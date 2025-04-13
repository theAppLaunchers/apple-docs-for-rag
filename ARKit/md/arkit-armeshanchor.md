

- ARKit
-  ARMeshAnchor 

Class

# ARMeshAnchor

An anchor for a physical object that ARKit detects and recreates virtually using a polygonal mesh.

iOS 13.4+iPadOS 13.4+Mac Catalyst 13.4+

``` source
class ARMeshAnchor
```

## Overview

ARKit subdivides the reconstructed, real-world scene surrounding the user into mesh anchors.

Mesh anchors constantly update their data as ARKit refines its understanding of the real world. Although ARKit updates a mesh to reflect a change in the physical environment (such as when a person pulls out a chair), the mesh’s subsequent change is not intended to reflect in real time.

## Topics

### Accessing the Mesh

var geometry: ARMeshGeometry

3D information about the mesh such as its shape and classifications.

class ARMeshGeometry

Mesh information stored in an efficient, array-based format.

## Relationships

### Inherits From

- ARAnchor

### Conforms To

- ARAnchorCopying
- CVarArg
- CustomDebugStringConvertible
- CustomStringConvertible
- Equatable
- Hashable
- NSCoding
- NSCopying
- NSObjectProtocol
- NSSecureCoding
- Sendable

## See Also

### Surface Detection

Tracking and visualizing planes

Detect surfaces in the physical environment and visualize their shape and location in 3D space.

class ARPlaneAnchor

An anchor for a 2D planar surface that ARKit detects in the physical environment.

