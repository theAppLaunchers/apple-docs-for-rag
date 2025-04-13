

- RealityKit
- USD Assets
- USDZ schemas for AR
-  Preliminary_ReferenceImage 

# Preliminary_ReferenceImage

A schema that defines the properties of an image in the physical environment.

## Overview

This schema defines the criteria that the runtime uses to recognize an image in the physical environment, including pixel data and width.

When RealityKit opens a USDZ file that defines a reference image, it instantiates an AnchorEntity with a component type AnchoringComponent.Target.image(group:name:).

### Declaration

```
class Preliminary_ReferenceImage "Preliminary_ReferenceImage" (
    inherits = 
)
```

### Define a reference image

The following example defines a prim named `ImageReference` that instructs the runtime to scan for an image described by `image.png`.

```
def Preliminary_ReferenceImage "ImageReference"
{
    uniform asset image = @image.png@
    uniform double physicalWidth = 12
}
```

## Topics

### Properties

image

An image file for which the runtime should search.

physicalWidth

An image’s width in centimeters.

## See Also

### Anchoring

Placing a prim in the real world

Anchor a prim to a real-world object that the runtime recognizes in the physical environment.

Preliminary_AnchoringAPI

A schema that defines the placement of a prim and its children at a real-world location.

