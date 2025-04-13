

- SceneKit
-  SCNParticleSystem 

Class

# SCNParticleSystem

An object that animates and renders a system of small image sprites using a high-level simulation whose general behavior you specify.

iOSiPadOSMac Catalyst 13.1+macOS 10.10+tvOSvisionOSwatchOS

``` source
class SCNParticleSystem
```

## Overview

Use particle systems to create effects such as smoke, rain, confetti, and fireworks.

### How Particle Systems Work

Unlike SceneKit nodes and geometries, individual particles are not objects in a scene graph. Because a particle system can involve dozens or hundreds of particles, SceneKit uses a more efficient internal representation that stores and processes the data for all of a system’s particles in bulk.

Instead of accessing each particle to control its behavior or to make it interact with other scene content, you typically use properties of a particle system to control the aggregate behavior of particles. These properties cover several key aspects of the system’s behavior, as summarized below.

- Appearance. SceneKit renders a texture image for each particle. Define the appearance of the particle system by specifying an image, its tint color, and rendering parameters such as blending mode. You can even specify an animated image sequence, creating effects like swarms of insects or multi-stage explosions.

- Life span. SceneKit creates each particle at a location in the scene (also called an *emitter*), varies its position and appearance over a specified life span, then removes it from the scene. (Particle creation is also called *birth* or *spawning*, and particle removal is also called *death*.) The total count of particles on screen at any time is the product of the system’s birthRate and particleLifeSpan properties. Larger numbers of particles have a greater cost to rendering performance and power usage.

- Emitter behavior. Use the emitterShape property to specify whether particles spawn from a single point in space or in the region defined by an SCNGeometry object. Use the emissionDuration property and related properties to vary particle birth over time, so that the system alternates between periods of spawning particles and periods of idle time.

- Variation. Particle systems simulate realistic effects by randomly varying particle properties both at birth and over the lifetime of a particle. You can also add random variation to the life span of particles. Several particle system properties have an associated variation property that controls this randomization. For example, the particleSizeVariation property defines the width of an interval for randomizing the particleSize property.

- Movement. Particles move according to a simple physics simulation—each has an initial direction, speed, angular velocity and acceleration, which SceneKit uses to animate the particle until it dies. You can create many realistic effects using these attributes alone. You can also add more complex behaviors by allowing particles to interact with scene geometry (colliderNodes), the scene’s physicsWorld simulation, or SCNPhysicsField objects.

In addition, you can also use the following features to add dynamic behaviors to a particle system, changing its appearance over time or making it interact with its environment.

- Animations and property controllers. Like many SceneKit objects, the SCNParticleSystem class conforms to the SCNAnimatable protocol, so you can implicitly or explicitly animate changes to its properties. (For general background on animation, see Animating SceneKit Content.) When you animate changes to a particle system’s properties, these changes affect all particles in the system simultaneously.

To apply animations independently for individual particles, use an SCNParticlePropertyController object, which associates a CAAnimation object with a particle system property. With a property controller, you can use features of the Core Animation framework to create time-varying effects that apply to each particle in the system. Typically a Core Animation object varies a property with respect to time, but with a property controller you can also create animations that vary a property based on other input values, such as a particle’s distance from its initial location.

For example, consider a CAKeyframeAnimation object that animates a series of colors from white to yellow to red, and a particle system that simulates a flame. If you attach this animation to a particle system’s particleColor property, the resulting flame effect has a single color at any given moment, but that color changes over time. If you instead attach a property controller for the color property, the flame varies in color from its base to its tip—each particle starts out white, then fades to yellow and red as it rises.

- Spawned particle systems. When you assign another SCNParticleSystem instance to one of the properties listed in Spawning Additional Particle Systems, SceneKit adds more particle systems to the scene based on the behavior of the original particle system. For example, if you have a particle system that simulates falling rain, you can use the systemSpawnedOnCollision property to add splashes where each raindrop strikes a surface.

- Event handlers and particle modifiers. Because they specify behavior declaratively, animations, property controllers, and spawned systems provide easy configuration and high performance for most dynamic behaviors. To create behaviors not possible with these features, you can register event handler or particle modifier blocks that work directly with the bulk particle data SceneKit uses to animate a particle system.

Use the handle(_:forProperties:handler:) method to modify particle data in response to an event—particle birth, death, or collision. For example, you can use this option to make particles that change color after colliding with another object in the scene.

Use the methods listed in Modifying Particles Over Time to manage blocks that SceneKit calls for every rendered frame. Your block can modify particle properties in bulk, allowing you to change particle behavior precisely, but at a high risk to rendering performance.

### Use the Xcode Particle System Editor to Experiment with Particle Systems

In most cases, you don’t need to configure a particle system directly in your app or game. Instead, you use Xcode to configure a particle system’s properties. As you change the behavior of the particle system, Xcode immediately provides an updated visual effect. When complete, Xcode archives the configured system into a file, which you can then include with your project’s bundle resources. Then, at runtime, your game uses this archive to instantiate a new particle system.

Using Xcode to create your particle systems has a few important advantages:

- You can easily learn the capabilities of the particle system class.

- You can experiment quickly with new particle effects and see the results immediately.

- You separate the task of designing a particle effect from the programming task of using it. Your artists can work on new particle effects independent of your game code.

- You can attach a particle system to a node in the Xcode scene editor to preview the particle system in your scene.

To load a particle system from a file you created with Xcode, use the init(named:inDirectory:) method.

## Topics

### Creating a Particle System

convenience init?(named: String, inDirectory: String?)

Loads a particle system from a file in the app’s bundle resources.

### Managing Particle Emission Timing

var emissionDuration: CGFloat

The duration, in seconds, over which the system spawns new particles. Animatable.

var emissionDurationVariation: CGFloat

The range, in seconds, of randomized emission duration values. Animatable.

var idleDuration: CGFloat

The duration, in seconds, of periods when the system emits no particles. Animatable.

var idleDurationVariation: CGFloat

The range, in seconds, of randomized idle duration values. Animatable.

var loops: Bool

A Boolean value that determines whether the system repeats its emission and idle periods.

var warmupDuration: CGFloat

The duration, in seconds, for which particles are spawned before the system is first rendered. Animatable.

var birthRate: CGFloat

The number of particles spawned during each emission period. Animatable.

var birthRateVariation: CGFloat

The range of randomized particle birth rate values. Animatable.

### Managing Particle Emission Locations

var emitterShape: SCNGeometry?

The shape of the region of space where the system spawns new particles.

var birthLocation: SCNParticleBirthLocation

The possible locations for newly spawned particles, relative to the emitter shape.

enum SCNParticleBirthLocation

Options for the initial location of each emitted particle, used by the birthLocation property.

var birthDirection: SCNParticleBirthDirection

The possible initial directions for newly spawned particles, relative to the emitter shape.

enum SCNParticleBirthDirection

Options for the initial direction of each emitted particle, used by the birthDirection property.

var emittingDirection: SCNVector3

The initial direction for newly spawned particles. Animatable.

var spreadingAngle: CGFloat

The range, in degrees, of randomized initial particle directions. Animatable.

### Managing Particle Motion

var particleAngle: CGFloat

The rotation angle, in degrees, of newly spawned particles. Animatable.

var particleAngleVariation: CGFloat

The range, in degrees of randomized initial particle angles. Animatable.

var particleVelocity: CGFloat

The initial speed, in units per second, for newly spawned particles. Animatable.

var particleVelocityVariation: CGFloat

The range, in units per second, of randomized initial particle speeds. Animatable.

var particleAngularVelocity: CGFloat

The initial spin rate, in degrees per second, of newly spawned particles. Animatable.

var particleAngularVelocityVariation: CGFloat

The range, in degrees per second, of randomized initial angular velocities for particles. Animatable.

var particleLifeSpan: CGFloat

The duration, in seconds, for which each particle is rendered before being removed from the scene. Animatable.

var particleLifeSpanVariation: CGFloat

The range, in seconds, of randomized particle life spans. Animatable.

### Specifying Particle Appearance

var particleSize: CGFloat

The rendered size, in units of the scene’s world coordinate space, of the particle image. Animatable.

var particleSizeVariation: CGFloat

The range of randomized particle sizes. Animatable.

var particleColor: UIColor

The color of newly spawned particles. Animatable.

var particleColorVariation: SCNVector4

The ranges of randomized particle color components. Animatable.

var particleImage: Any?

The texture image SceneKit uses to render each particle.

var fresnelExponent: CGFloat

The reflectivity exponent SceneKit uses when rendering the particle’s image as a cube map. Animatable.

var stretchFactor: CGFloat

A multiplier for stretching particle images along their direction of motion. Animatable.

### Animating Particle Images

var imageSequenceRowCount: Int

The number of rows for treating the particle image as a grid of animation frames.

var imageSequenceColumnCount: Int

The number of columns for treating the particle image as a grid of animation frames.

var imageSequenceInitialFrame: CGFloat

The index of the first frame in a particle image animation. Animatable.

var imageSequenceInitialFrameVariation: CGFloat

The range of randomized initial frames for particle image animation. Animatable.

var imageSequenceFrameRate: CGFloat

The rate, in frames per second, of particle image animation. Animatable.

var imageSequenceFrameRateVariation: CGFloat

The range, in frames per second, of randomized frame rates for particle image animation. Animatable.

var imageSequenceAnimationMode: SCNParticleImageSequenceAnimationMode

The animation mode for particle image animation.

enum SCNParticleImageSequenceAnimationMode

Options for animating each particle with a sequence of images, used by the imageSequenceAnimationMode property.

### Simulating Physics for Particles

var isAffectedByGravity: Bool

A Boolean value that determines whether gravity, as defined by the scene’s physics simulation, affects the motion of particles.

var isAffectedByPhysicsFields: Bool

A Boolean value that determines whether physics fields in the scene affect the motion of particles.

var colliderNodes: [SCNNode]?

The nodes whose geometry the system’s particles can collide with.

var particleDiesOnCollision: Bool

A Boolean value that determines whether particles are removed from the scene upon colliding with another object.

var acceleration: SCNVector3

The constant acceleration vector, in units per second per second, applied to all particles in the system. Animatable.

var dampingFactor: CGFloat

A factor that slows particles relative to their velocity. Animatable.

var particleMass: CGFloat

The mass, in kilograms, of each particle in the system. Animatable.

var particleMassVariation: CGFloat

The range, in kilograms, of randomized particle masses. Animatable.

var particleCharge: CGFloat

The electric charge, in coulombs, of each particle in the system. Animatable.

var particleChargeVariation: CGFloat

The range, in coulombs, of randomized particle charges. Animatable.

var particleBounce: CGFloat

The restitution coefficient of each particle in the system. Animatable.

var particleBounceVariation: CGFloat

The range of randomized restitution coefficients for particles. Animatable.

var particleFriction: CGFloat

The friction coefficient of each particle in the system. Animatable.

var particleFrictionVariation: CGFloat

The range of randomized friction coefficients for particles. Animatable.

### Spawning Additional Particle Systems

var systemSpawnedOnCollision: SCNParticleSystem?

Another particle system to be added to the scene when a particle collides with scene geometry.

var systemSpawnedOnDying: SCNParticleSystem?

Another particle system to be added to the scene when a particle dies.

var systemSpawnedOnLiving: SCNParticleSystem?

Another particle system to be added to the scene for each living particle in the system.

### Managing Particle Rendering

var blendMode: SCNParticleBlendMode

The blending mode for compositing particle images into the rendered scene.

enum SCNParticleBlendMode

Options for combining source and destination pixel colors when compositing particles during rendering, used by the blendMode property.

var orientationMode: SCNParticleOrientationMode

The mode defining whether and how particles may rotate.

enum SCNParticleOrientationMode

Options for restricting the orientation of particles, used by the orientationMode property.

var sortingMode: SCNParticleSortingMode

The mode defining the order in which SceneKit renders the system’s particles.

enum SCNParticleSortingMode

Options for the rendering order of particles, used by the sortingMode property.

var isLightingEnabled: Bool

A Boolean value that determines whether SceneKit applies lighting to particle images when rendering.

var isBlackPassEnabled: Bool

A Boolean value that determines whether SceneKit renders particles in black before rendering the particle image.

### Controlling Particle Simulation

var isLocal: Bool

A Boolean value that specifies whether the particle simulation runs in the local coordinate space of the node containing it.

func reset()

Returns the particle system to its initial state.

var speedFactor: CGFloat

A multiplier for the speed at which SceneKit runs the particle simulation. Animatable.

### Modifying Particles in Response to Particle System Events

func handle(SCNParticleEvent, forProperties: [SCNParticleSystem.ParticleProperty], handler: SCNParticleEventBlock)

Adds a block that modifies particle properties, to be executed at a specified event in the lifetimes of particles in the system.

enum SCNParticleEvent

Significant events in the life spans of simulate particles, used by the handle(_:forProperties:handler:) method.

typealias SCNParticleEventBlock

The signature for blocks called by SceneKit in response to significant events during particle simulation, used by the handle(_:forProperties:handler:) method.

### Modifying Particles Over Time

var propertyControllers: [SCNParticleSystem.ParticleProperty : SCNParticlePropertyController]?

A dictionary that optionally associates particle properties with objects that animate a property’s value for each particle.

func addModifier(forProperties: [SCNParticleSystem.ParticleProperty], at: SCNParticleModifierStage, modifier: SCNParticleModifierBlock)

Adds a block that modifies particle properties, to be executed each time SceneKit renders a frame.

func removeModifiers(at: SCNParticleModifierStage)

Removes particle modifier blocks for the specified stage of the particle simulation.

func removeAllModifiers()

Removes all particle modifier blocks associated with the particle system.

struct ParticleProperty

Keys identifying properties of individual particles, used by the propertyControllers dictionary and the handle(_:forProperties:handler:) and addModifier(forProperties:at:modifier:) methods.

enum SCNParticleModifierStage

Stages of SceneKit’s particle simulation process into which you can insert modifier blocks, used by the addModifier(forProperties:at:modifier:) method.

typealias SCNParticleModifierBlock

The signature for blocks called by SceneKit to modify particle properties on each frame of simulation, used by the addModifier(forProperties:at:modifier:) method.

### Sample Code

Example projects making use of SceneKit particle systems.

Building a document browser app for custom file formats

Implement a custom document file format to manage user interactions with files on different cloud storage providers.

### Instance Properties

var orientationDirection: SCNVector3

var particleIntensity: CGFloat

var particleIntensityVariation: CGFloat

var writesToDepthBuffer: Bool

## Relationships

### Inherits From

- NSObject

### Conforms To

- CVarArg
- CustomDebugStringConvertible
- CustomStringConvertible
- Equatable
- Hashable
- NSCoding
- NSCopying
- NSObjectProtocol
- NSSecureCoding
- SCNAnimatable

## See Also

### Particle Systems

class SCNParticlePropertyController

An animation for a single property of the individual particles rendered by a particle system.

