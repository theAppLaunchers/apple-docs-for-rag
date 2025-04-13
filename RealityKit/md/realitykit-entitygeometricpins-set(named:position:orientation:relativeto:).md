

- RealityKit
- EntityGeometricPins
-  set(named:position:orientation:relativeTo:) 

Instance Method

# set(named:position:orientation:relativeTo:)

Creates and adds a geometric pin to the entity, and returns the entity geometric pin.

iOS 18.0+iPadOS 18.0+Mac Catalyst 18.0+macOS 15.0+visionOS 2.0+

``` source
@discardableResult @MainActor
func set(
    named name: String,
    position: SIMD3 = SIMD3(0, 0, 0),
    orientation: simd_quatf = simd_quatf(ix: 0, iy: 0, iz: 0, r: 1),
    relativeTo referenceEntity: Entity?
) -> GeometricPin
```

## Parameters 

`name`  

The name of the pin in the namespace of the owning entity.

`position`  

The position of the pin, in local space of the reference entity.

`orientation`  

The orientation of the pin, in local space of the reference entity.

`referenceEntity`  

The entity that specifies the space of input `position` and `orientation`. The input `position` and `orientation` are in the world space when this reference entity is `nil`.

## Return Value

A `GeometricPin`, identifying the newly added reference frame on the Entity.

## Discussion

The pin is added to the entity’s GeometricPinsComponent.

