

- RealityKit
-  BlendShapeWeightsMapping 

Class

# BlendShapeWeightsMapping

A mapping of blend weights to the target meshes that those weights affect.

iOS 18.0+iPadOS 18.0+Mac Catalyst 18.0+macOS 15.0+visionOS 2.0+

``` source
class BlendShapeWeightsMapping
```

## Overview

Use `BlendShapeWeightsMapping` to initialize a BlendShapeWeightsComponent. You can initialize it in two different ways:

- Initialize the mapping from a user-provided MeshResource, from which the mapping information can be generated. In this case, the number of blend shapes and each blend shape’s weights map exactly to the `MeshResource`’s structure.

```
if let modelComponent = blendShapeEntity.components[ModelComponent.self] {
    let meshResource = modelComponent.mesh
    let blendShapeWeightsMapping = BlendShapeWeightsMapping(
        meshResource: meshResource)
    blendShapeEntity.components.set(BlendShapeWeightsComponent(
        weightsMapping: blendShapeWeightsMapping))
}
```

- Initialize the mapping from a user-defined blend shape name and list of weight names. When used to initialize a BlendShapeWeightsComponent, the weight names define which mesh targets map from the owning entity’s ModelComponent’s mesh resource.

  RealityKit expects the ModelComponent to already be assigned to the entity on which the BlendShapeWeightsComponent resides. Match the weight names to the weight names found in the ModelComponent’s mesh resource. If a weight name does not match any of the mesh weight names then it is ignored and that weight will have no effect. If a weight name in the ModelComponent’s mesh resource is excluded from the list of weight names, then the associated target mesh will not be controllable by any of the provided weights.

  Note also that the provided blend shape name can be used to reference the blend shape weights in the BlendShapeWeightsSet.

```
let weightNames: [String] = [
    "weight0",
    "weight1"
]

let blendShapeWeightsMapping = BlendShapeWeightsMapping(
    blendShapeName: "BlendShape0",
    weightNames: weightNames)

blendShapeEntity.components.set(BlendShapeWeightsComponent(
    weightsMapping: blendShapeWeightsMapping))
```

## Topics

### Initializers

init(blendShapeName: String, weightNames: [String])

Creates a mapping that applies the weight names to mesh parts in a model component.

init(meshResource: MeshResource)

Creates a mapping from the given MeshResource.

## Relationships

### Conforms To

- Resource
- Sendable

## See Also

### Blend shape management

struct BlendShapeWeightsComponent

A component that provides access to the current weights associated with all blend shape meshes on an entity.

struct BlendShapeWeights

A set of animatable weight values that collectively represent the blending amounts for all the blend shapes’ blend targets.

struct BlendShapeWeightsData

A structure that encapsulates the blend shape name, blend shape weights and the names of those weights to be stored by the blend shape weights set.

struct BlendShapeWeightsSet

A custom collection of named blend shape weights.

