

- RealityKit
- USD Assets
- USDZ schemas for AR
- Preliminary_AnchoringAPI
-  preliminary:planeAnchoring:alignment 

Article

# preliminary:planeAnchoring:alignment

An option that specifies the orientation of a plane.

## Overview

This property is active only for the `preliminary:anchoring:type` value `plane`. The runtime recognizes real-word surfaces such as floors, tables, ceilings as horizontal planes. Vertical planes include walls, doors, and windows.

### Declaration

```
uniform token preliminary:planeAnchoring:alignment (
        allowedTokens = ["horizontal", "vertical", "any"]
)
```

### Plane anchor types

`horizontal`  
Requests that the runtime anchor the prim on a floor, table, ceiling, or other flat surface.

`vertical`  
Requests that the runtime anchor the prim on a wall, door, window, or other vertical surface.

`any`  
Requests that the runtime anchor the prim on the first horizontal or vertical surface detected.

### Anchor a prim to a horizontal plane

The following asset definition requests that the runtime anchor this prim to the first surface the runtime detects that occupies a horizontal orientation in relation to the camera.

```
def Cube "PlaneAnchoredCube" (
    prepend apiSchemas = [ "Preliminary_AnchoringAPI" ]
)
{
    uniform token preliminary:anchoring:type = "plane"
    uniform token preliminary:planeAnchoring:alignment = "horizontal"
    ...
}
```

## See Also

### Properties

preliminary:anchoring:type

A option that specifies the type of anchor.

preliminary:imageAnchoring:referenceImage

The characteristics of an image the runtime should scan for in order to attach a prim.

