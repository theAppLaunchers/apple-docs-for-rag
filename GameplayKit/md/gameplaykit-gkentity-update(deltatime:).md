

- GameplayKit
- GKEntity
-  update(deltaTime:) 

Instance Method

# update(deltaTime:)

Performs periodic updates for each of the entity’s components.

iOS 9.0+iPadOS 9.0+Mac Catalyst 13.1+macOS 10.11+tvOS 9.0+visionOS 1.0+

``` source
func update(deltaTime seconds: TimeInterval)
```

## Parameters 

`seconds`  

The time step to use for any time-dependent actions performed by this method (typically, the elapsed time since the previous call to this method).

## Discussion

At runtime, an entity/component-based game needs to dispatch periodic logic—from an update/render loop method such as update(_:) (SpriteKit) or renderer(_:updateAtTime:) (SceneKit), or a CADisplayLink (iOS) or CVDisplayLink (macOS) timer in a custom rendering engine—to each of its components, so that each can perform component-specific update logic.

The GKEntity update(deltaTime:) method is one of the two options GameplayKit provides for dispatching updates—this option is easy to implement in games with small numbers of entities and components. Call this method for each entity in your game, and each entity will in turn call the update(deltaTime:) method for each of its components.

The other option is to dispatch updates per-component, rather than per-entity, using a GKComponentSystem object. Using a component system allows you to update all components of a specific component class in a deterministic order, without needing to traverse your game’s object graph and update each entity.

Note

If a component owned by an entity is a member of a component system, calling the entity’s update(deltaTime:) method will not update that component.

