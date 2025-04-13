

- RealityKit
- EntityGeometricPins
-  set(named:skeletalJointName:position:orientation:) 

Instance Method

# set(named:skeletalJointName:position:orientation:)

Creates and adds a geometric pin to the entity’s skeletal joint, and returns the geometric pin.

iOS 18.0+iPadOS 18.0+Mac Catalyst 18.0+macOS 15.0+visionOS 2.0+

``` source
@discardableResult @MainActor
func set(
    named name: String,
    skeletalJointName: String,
    position: SIMD3 = SIMD3(0, 0, 0),
    orientation: simd_quatf = simd_quatf(ix: 0, iy: 0, iz: 0, r: 1)
) -> GeometricPin
```

## Parameters 

`name`  

Name of the `GeometricPin` in the namespace of the owning entity.

`skeletalJointName`  

The name of the skeletal joint in the namespace of the owning entity.

`position`  

The position of the pin, in local space of the joint.

`orientation`  

The orientation of the pin, in local space of the joint.

## Return Value

A `GeometricPin`, identifying the newly added reference frame on the Entity.

## Discussion

The pin is added to the entity’s GeometricPinsComponent.

