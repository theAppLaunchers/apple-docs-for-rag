

- RealityKit
- Entity
-  convert(transform:to:) 

Instance Method

# convert(transform:to:)

Converts the scale, rotation, and position of a transform from the local space of the entity on which you called this method to the local space of a reference entity.

iOS 13.0+iPadOS 13.0+Mac Catalyst 13.0+macOS 10.15+visionOS

``` source
@MainActor @preconcurrency
func convert(
    transform: Transform,
    to referenceEntity: Entity?
) -> Transform
```

## Parameters 

`transform`  

The transform given in the local space of the entity.

`referenceEntity`  

The entity that defines a frame of reference. Set this to `nil` to indicate world space.

## Return Value

The transform specified relative to `referenceEntity`.

