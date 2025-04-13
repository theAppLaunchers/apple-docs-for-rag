

- RealityKit
-  Systems 

API Collection

# Systems

Apply behaviors and physical effects to the entities in a RealityKit scene.

## Overview

In the Entity-Component-System (ECS) paradigm, the behavior of entities is often implemented using *systems*. A System has an update(context:) method that fires every frame and applies its logic to all entities that meet certain criteria. For example, a game might have a system that controls applying damage to entities from different sources. The same system might make changes to the player’s character, non-player characters, and even inanimate objects that can be damaged or broken. Systems typically work together with one or more components. The system’s component both identifies which entities the system effects and also stores any per-entity data the system needs to work. A damage system, for example, might work with a damage component that stores health or hit points. To make an entity damageable, all you have to do is add the damage component to it, which can be done at runtime. The damage system queries for entities that contain the damage component and applies the appropriate health or hit point change to each of them.

In traditional object-oriented design, the behavior of an object is usually implemented by writing methods on each object. Using that approach, the code to apply damage to an entity would reside on the entity subclasses. There are two drawbacks to the traditional approach when it comes to the design of games and other immersive experiences.

First, if multiple objects require the same behavior, but are implemented as different entity classes without a common ancestor other than Entity, that logic has to be duplicated on all the objects and the duplicated code has to be kept in sync as it changes.

Second, having to call behavior methods individually on every relevant entity in the scene can negatively impact performance. By placing logic that potentially effects multiple types of entities into a single System, we reduce the overhead required to implement the logic. It also allows us to do any per-frame calculations that are the same for all entities only once per frame, eliminating the need to do those calculations for every entity in the scene that can be damaged.

## Topics

### System configuration

Implementing systems for entities in a scene

Apply behaviors and physical effects to the objects and characters in a RealityKit scene with the Entity Component System (ECS).

protocol System

An object that affects multiple entities in every update of a RealityKit scene.

struct SystemUpdateCondition

A condition which causes a system to update.

struct SceneUpdateContext

An object that contains information about the scene to update.

### Entity queries

struct EntityQuery

An object that retrieves entities from a scene.

struct QueryPredicate

An object that defines the criteria for an entity query.

struct QueryResult

An object that returns the results of an entity query.

## See Also

### Scene management and logic

Scenes

The context that holds all RealityKit entities.

Events

Respond to things happening in your RealityKit scene by subscribing to specific event types.

Entity actions

Create simple, reusable actions that can change your app state, RealityKit scene, or animate an entity.

