

- RealityKit
-  ModelSortGroup 

Structure

# ModelSortGroup

A group that you assign to multiple entities to tell the renderer what order and how to render the entities in the group.

iOS 18.0+iPadOS 18.0+Mac Catalyst 18.0+macOS 15.0+visionOS 1.0+

``` source
struct ModelSortGroup
```

## Overview

Each model sort group relates model entities to each other so that you can define what order the renderer draws them. Pass the same model sort group instance to each ModelSortGroupComponent whose entity you want to group, along with an order number for that entity within the group.

```
let group1 = ModelSortGroup()
entityA.components.set(
    ModelSortGroupComponent(group: group1, order: 0)
)
entityB.components.set(
    ModelSortGroupComponent(group: group1, order: 1)
)
```

In the example above, the renderer draws `entityA` before `entityB`.

Each `ModelSortGroup` instance represent a unique group.

```
let group2 = ModelSortGroup()
entityC.components.set(
    ModelSortGroupComponent(group: group2, order: 2)
)
entityD.components.set(
    ModelSortGroupComponent(group: group2, order: 3)
)
```

In this example, `entityC` and `entityD` are in the same group as each other, but in a different group than `entityA` and `entityB`.

## Topics

### Operators

static func != (ModelSortGroup, ModelSortGroup) -> Bool

Returns a Boolean that indicates whether the model sort groups are unequal.

static func == (ModelSortGroup, ModelSortGroup) -> Bool

Returns a Boolean that indicates whether the model sort groups are equal.

### Initializers

init(depthPass: ModelSortGroup.DepthPass?)

Creates a model sort group with an optional depth pass.

### Instance Properties

var depthPass: ModelSortGroup.DepthPass?

A depth pass that controls when the renderer draws the depth of model entities in the group relative to their color.

var planarUIPlacement: ModelSortGroup.PlanarUIPlacement?

A planar placement instance that controls how the renderer draws a model relative to a planar mesh or a SwiftUI view that’s coplanar and overlapping.

### Type Properties

static let planarUIAlwaysBehind: ModelSortGroup

A model sort group that instructs the renderer to draw a model’s mesh behind a SwiftUI layer that’s coincident with the mesh. See ModelSortGroup.PlanarUIPlacement for usage.

static let planarUIAlwaysInFront: ModelSortGroup

A model sort group that instructs the renderer to draw a model’s mesh in front of a SwiftUI layer that’s coincident with the mesh. See ModelSortGroup.PlanarUIPlacement for usage.

static let planarUIInline: ModelSortGroup

A model sort group that instructs the renderer to draw a model’s mesh along with a SwiftUI layer that’s coincident with the mesh. See ModelSortGroup.PlanarUIPlacement for usage.

### Enumerations

enum DepthPass

Options that indicate when the renderer draws a model’s depth relative to its color.

enum PlanarUIPlacement

A set of predefined groups that indicate how the renderer draws a model relative to a planar mesh or a SwiftUI view that’s coplanar and overlapping.

### Default Implementations

Equatable Implementations

## Relationships

### Conforms To

- Equatable
- Sendable

## See Also

### Render configuration

struct ModelSortGroupComponent

A component that configures the rendering order for an entity’s model.

struct OpacityComponent

A component that controls the opacity of an entity and its descendants.

struct AdaptiveResolutionComponent

A component that provides the suggested pixels per meter necessary to render an object.

struct ModelDebugOptionsComponent

A component that changes how RealityKit renders its entity to help with debugging.

