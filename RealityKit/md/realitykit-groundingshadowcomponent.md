

- RealityKit
-  GroundingShadowComponent 

Structure

# GroundingShadowComponent

A component that controls an entity’s grounding shadow.

iOS 18.0+iPadOS 18.0+Mac Catalyst 18.0+macOS 15.0+visionOS 1.0+

``` source
struct GroundingShadowComponent
```

## Overview

A grounding shadow is an effect that makes an entity look like it has a light source directly above it. You can add a grounding shadow to any entity that has a ModelComponent in its component set by adding a grounding shadow component to the entity’s components property.

```
if let model = try? await ModelEntity(named: "tv_retro") {
    let shadowComponent = GroundingShadowComponent(castsShadow: true)
    model.components.set(shadowComponent)
}
```

| Without shadow | With shadow |
|----|----|
|  |  |

You need to add the grounding shadow component to each entity you want to apply the effect to, because the grounding shadow component doesn’t apply to hierarchies.

Note

Neither virtual nor physical light sources affect grounding shadows.

### Receiving Shadows

By default, all entity models with a grounding shadow component can cast a shadow onto any other model entities in the scene. However, you can configure an entity to opt out of receiving shadows from other entities by setting a grounding shadow component’s receivesShadow property to `false` and adding that component to the entity that’s opting out.

```
let tvShadow = GroundingShadowComponent(castsShadow: true)
tvShadow.receivesShadow = false
tv.components.set(tvShadow)
```

Alternatively, you can create a new grounding shadow component instance that opts out of receiving shadows by passing `false` to the `receivesShadow` parameter of the init(castsShadow:receivesShadow:) initializer.

```
let robotShadow = GroundingShadowComponent(castsShadow: true,
                                           receivesShadow: false)
robot.components.set(robotShadow)
```

| Receiving shadows | Not receiving shadows |
|----|----|
|  |  |

RealityKit generates grounding shadows from the perspective of another entity that receives the first entity’s shadow. One-sided geometry only casts a shadow if its facets face the entity that receives the shadow, which typically means they face downward. Make each 2D object cast a grounding shadow by applying a material that disables face culling, or by replacing it with a watertight mesh.

## Topics

### Initializers

init(castsShadow: Bool)

Creates a grounding shadow component.

init(castsShadow: Bool, receivesShadow: Bool)

Creates a grounding shadow component by configuring whether its entity receives shadows from other model entities with the component.

init(castsShadow: Bool, receivesShadow: Bool, fadeBehaviorNearPhysicalObjects: GroundingShadowComponent.FadeBehaviorNearPhysicalObjects)

Creates a grounding shadow component by configuring whether its entity receives shadows and its fade behavior near physical objects.

### Instance Properties

var castsShadow: Bool

A Boolean value that indicates whether an entity casts a shadow onto other model entities in the scene.

var fadeBehaviorNearPhysicalObjects: GroundingShadowComponent.FadeBehaviorNearPhysicalObjects

Configures the grounding shadow’s fade behavior when the entity is near physical objects.

var receivesShadow: Bool

A Boolean value that indicates whether an entity with the grounding shadow component receives grounding shadows from other model entities.

### Enumerations

enum FadeBehaviorNearPhysicalObjects

Describes the behavior of an entity’s grounding shadow when it’s near physical objects.

### Default Implementations

Component Implementations

## Relationships

### Conforms To

- Component

## See Also

### General shadows

struct DynamicLightShadowComponent

A component that controls an entity’s shadow from dynamic (virtual) lights.

