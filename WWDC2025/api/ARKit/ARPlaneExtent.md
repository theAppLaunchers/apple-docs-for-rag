*   [ARKit](/documentation/arkit)
*   ARPlaneExtent

Class

# ARPlaneExtent

The size and y-axis rotation of a detected plane.

iOS 16.0+iPadOS 16.0+Mac Catalyst 16.0+

```swift
```swift
```swift
```swift
```swift
```swift
```swift
```swift
class ARPlaneExtent
```
```
```
```
```
```
```
```

## [Overview](/documentation/ARKit/ARPlaneExtent#overview)

A plane anchor ([`ARPlaneAnchor`](/documentation/arkit/arplaneanchor)) describes its size and orientation on the y-axis using the [`planeExtent`](/documentation/arkit/arplaneanchor/planeextent) property of this type.

At runtime, ARKit continually updates the anchor’s width and height as the framework refines its knowledge of the plane’s shape in the environment.

Similarly, as the session runs, the framework may update the plane’s y-rotation to better fit its rectangular area in the environment. In iOS 15 and earlier, the framework rotates the plane anchor according to that angle. In iOS 16, the framework doesn’t rotate the anchor automatically and its transform matrix remains unchanged. Instead, the framework exposes the angle [`rotationOnYAxis`](/documentation/arkit/arplaneextent/rotationonyaxis) that you apply to any plane extent geometry in your app.

Important

Apps that run on iOS 16 with a deployment target less than iOS 16 preserve the prior y-axis rotation behavior.

### [Size and Rotate an Entity to a Plane’s Extent](/documentation/ARKit/ARPlaneExtent#Size-and-Rotate-an-Entity-to-a-Planes-Extent)

The following code defines a RealityKit entity sized to the plane extent’s width and height. The helper function also applies the extent’s suggested y-axis rotation by setting its transform `yaw` value to [`rotationOnYAxis`](/documentation/arkit/arplaneextent/rotationonyaxis).

```swift
```swift
```swift
```swift
```swift
```swift
func createPlane(for planeAnchor: ARPlaneAnchor, material: Material) -> ModelEntity {
```
```
    // Get the plane's extent.
    let extent = planeAnchor.planeExtent
    // Create a model entity sized to the plane's extent.
    let planeEntity = ModelEntity(mesh: .generatePlane (width: extent.width, depth: extent.height),
        materials: [material])
    // Orient the entity according to the extent's y-axis rotation.
    planeEntity.transform = Transform(pitch: 0, yaw: extent.rotationOnYAxis, roll: 0)
    // Center the entity on the plane.
    planeEntity.transform.translation = planeAnchor.center
    return planeEntity
}
```
```
```
```

## [Topics](/documentation/ARKit/ARPlaneExtent#topics)

### [Inspecting Plane Size](/documentation/ARKit/ARPlaneExtent#Inspecting-Plane-Size)

```swift
```swift
```swift
```swift
var width: Float
```
```

The estimated width of the plane.
```
```swift
```swift
```swift
var height: Float
```
```

The estimated height of the plane.
```
```

### [Inspecting Plane Y-Rotation](/documentation/ARKit/ARPlaneExtent#Inspecting-Plane-Y-Rotation)

```swift
```swift
```swift
```swift
var rotationOnYAxis: Float
```
```

A radian value that indicates a plane’s y-axis orientation.
```
```

## [Relationships](/documentation/ARKit/ARPlaneExtent#relationships)

### [Inherits From](/documentation/ARKit/ARPlaneExtent#inherits-from)

*   [`NSObject`](/documentation/ObjectiveC/NSObject-swift.class)

### [Conforms To](/documentation/ARKit/ARPlaneExtent#conforms-to)

*   [`CVarArg`](/documentation/Swift/CVarArg)
*   [`CustomDebugStringConvertible`](/documentation/Swift/CustomDebugStringConvertible)
*   [`CustomStringConvertible`](/documentation/Swift/CustomStringConvertible)
*   [`Equatable`](/documentation/Swift/Equatable)
*   [`Hashable`](/documentation/Swift/Hashable)
*   [`NSCoding`](/documentation/Foundation/NSCoding)
*   [`NSObjectProtocol`](/documentation/ObjectiveC/NSObjectProtocol)
*   [`NSSecureCoding`](/documentation/Foundation/NSSecureCoding)
*   [`Sendable`](/documentation/Swift/Sendable)
*   [`SendableMetatype`](/documentation/Swift/SendableMetatype)

## [See Also](/documentation/ARKit/ARPlaneExtent#see-also)

### [Dimensions](/documentation/ARKit/ARPlaneExtent#Dimensions)

```swift
```swift
```swift
```swift
var center: simd_float3
```
```

The center point of the plane relative to its anchor position.
```
```swift
```swift
```swift
var planeExtent: ARPlaneExtent
```
```

The estimated width, length, and y-axis rotation of the detected plane.
```
```swift
```swift
```swift
var extent: simd_float3
```
```

The estimated width and length of the detected plane.

Deprecated
```
```