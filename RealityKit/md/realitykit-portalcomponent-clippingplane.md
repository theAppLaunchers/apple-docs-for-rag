

- RealityKit
- PortalComponent
-  clippingPlane 

Instance Property

# clippingPlane

The clipping plane of the portal, using the entity’s local coordinates.

iOS 18.0+iPadOS 18.0+Mac Catalyst 18.0+macOS 15.0+visionOS 1.0+

``` source
var clippingPlane: PortalComponent.ClippingPlane? { get set }
```

## Discussion

When you define this property, the portal clips meshes inside the world, which are in front of the clipping plane.

