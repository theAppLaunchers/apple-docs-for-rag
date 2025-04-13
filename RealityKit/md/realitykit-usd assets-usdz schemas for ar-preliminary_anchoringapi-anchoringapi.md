

- RealityKit
- USD Assets
- USDZ schemas for AR
-  Preliminary_AnchoringAPI 

# Preliminary_AnchoringAPI

A schema that defines the placement of a prim and its children at a real-world location.

## Overview

Use this schema to attach prims to real-world areas in an AR experience, such as surfaces, images, or faces. In non-AR viewers like studio mode in AR Quick Look, the runtime displays a prim by applying its *transform* –– that is, its position, rotation, and scale –– relative to the center of the view.

Note

Although ARKit features the ability to recognize predefined real-world objects (see ARReferenceObject), and location anchors (see ARGeoAnchor), the Preliminary_AnchoringAPI schema doesn’t support object or location anchors.

### Declaration

```
class "Preliminary_AnchoringAPI"
(
    inherits = 
)
```

### Nest and layer anchorable prims

When you assign this schema to a nested prim, the runtime positions the nested prim independently by not basing the child’s transform relative to its parent. As a result, the anchorable child is effectively out of the parent’s hierarchy. Similarly, if an asset defines one or more anchorable prims layered beneath another anchorable prim, the runtime positions each prim independently. However, any unanchorable children of an anchorable prim remain positioned relative to their parent.

Since the runtime doesn’t observe anchorable prim hierarchies, you need to define all anchorable prims at the root of the document, thus, without a parent.

## Topics

### Properties

preliminary:anchoring:type

A option that specifies the type of anchor.

preliminary:planeAnchoring:alignment

An option that specifies the orientation of a plane.

preliminary:imageAnchoring:referenceImage

The characteristics of an image the runtime should scan for in order to attach a prim.

## See Also

### Anchoring

Placing a prim in the real world

Anchor a prim to a real-world object that the runtime recognizes in the physical environment.

Preliminary_ReferenceImage

A schema that defines the properties of an image in the physical environment.

