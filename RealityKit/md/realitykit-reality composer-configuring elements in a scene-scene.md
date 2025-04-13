

- RealityKit
- Reality Composer
-  Configuring elements in a scene 

Article

# Configuring elements in a scene

Define the appearance and behavior of objects in a scene.

## Overview

You can configure Reality Composer assets in a number of different ways. You can assign them unique names, change their appearance, or configure them to simulate real-world physics.

### Name the assets and scenes

Reality Composer allows you to assign a name to your scenes, as well as to objects within a scene. You can use the names in your code to retrieve specific scenes or assets, and Xcode uses the assigned names during code generation.

Reality Composer creates a unique, default name for any newly created scene. Change the default value to something descriptive to make your code easier to understand. Tap the scene background to deselect any selected objects, and change the scene’s name using the top-most text field in the inspector.

You can also assign names to a scene’s objects to help differentiate them. To assign or change an object’s name, tap the object to select it, then type the name into the name field at the top of the Properties inspector. Xcode automatically generates accessor properties for all named assets. Unique object names aren’t required, but objects with the same name in the same scene are automatically grouped into a single array property during code generation.

Important

Code generation fails if you use a scene name more than once in the same target. If you’re using multiple reality files in the same Xcode target, make sure your scene names are unique across all reality files.

### Style an asset to match your scene’s look

When you select a built-in Reality Composer asset, the Properties inspector displays a section called Look, where you change the asset’s overall appearance. In this section, you’ll find either a parameter called Material, for simple shape primitives, or a parameter called Style, for modeled assets.

The Material parameter defines the overall surface appearance of the selected object. You choose from many predefined physically based rendering (PBR) materials. Some of these materials, like Glossy Paint, Matte Paint, and Car Paint, allow you to select a color using the Material Color parameter, while others, like Gold and Rubber, use a predefined color.

The Style parameter lets you choose from many predefined appearances. Many assets, for example, let you choose between Realistic, Stylized, or Iconic. The realistic style is designed to be a very natural-looking object, often even including scratches or smudges to make the item fit in with its real-world surroundings. The stylized option creates an object that has fewer real-world details, and the iconic style creates an even less realistic object that makes no attempt to look like it belongs in the real world.

### Modify procedural asset parameters in scene view

When you use Reality Composer’s built-in assets, you can visually modify some of the configurable parameters in the scene using Reality Composer’s Modify mode. When in this mode, the manipulator changes to display blue disc-shaped handles that you can use to alter the appearance of the selected asset. The number and effect of these handles varies with the type of asset. The handles on a cube, for example, allow you to drag different handles to change the cube’s proportions, by separately modifying its height, width, and depth.

To switch to Modify mode on the Mac, select the object you want to edit, choose the Modify button in the toolbar, and select Modify from the Arrange menu or the contextual menu. On iOS devices, select the object you want to edit, then choose the Modify button in the toolbar.

### Use physics and gravity in a scene

Reality Composer scenes can simulate real-world physics behavior, such as gravity and object collisions. Objects in a scene that participate in the physics simulation can interact with each other or with detected real-world surfaces, such as tables, walls, and floors. By default, Reality Composer scenes have physics and gravity enabled, but objects you add to a scene do not participate in the physics simulation unless you specifically configure them to do so.

To enable physics for an object, select it to bring up its Properties inspector. The bottom-most section in the inspector is labeled “Physics.” For a newly added object, this section contains a single checkbox labeled “Participates.” Select this checkbox to add this object to the physics simulation.

When you enable the Participates checkbox, three new options appear in the Physics section of the Properties inspector:

**Motion Type.** Defines how physics work for the selected object. Two options are available: *Fixed* and *Dynamic*. When an object’s motion type is set to Fixed, other objects in the scene can collide with it, but it stays in the same place, unaffected by those collisions. When an object’s Motion Type is set to Dynamic, it participates fully in the physics simulation. If, for example, a dynamic object is not resting on a surface, the scene’s gravity makes it fall until it lands on a surface or another object. When you apply forces to a dynamic object, or a dynamic object collides with another object, it moves.

**Material.** Defines how the object behaves when colliding with other objects, basing its behavior on real-world substances like concrete and rubber. The physics material determines how heavy an object is based on its size. It also determines how the object reacts when it collides with another object or a detected surface. A rubber object, for example, bounces higher than a lead object of the same size.

Note

An object’s Material parameter in the Physics section of the inspector is completely distinct from the Material parameter in the Look section. The physics material defines the properties of the object that are important to the physics simulation, such as the mass and elasticity (or “bounciness”) of the object, while the look material defines how the object is rendered. It is entirely possible to create an asset that looks like one material and behaves like a completely different material.

**Collision Shape.** Used when RealityKit performs physics simulations on the object. Because physics calculations for complex shapes are computationally expensive, RealityKit uses a simplified shape like a box or sphere instead of the object’s actual shape when doing physics calculations. You can select Automatic to let RealityKit choose a collision shape, or you can manually select the shape that will give the behavior you want.

## See Also

### Scene creation

Creating 3D Content with Reality Composer

Assemble assets into a dynamic 3D composition that you can add to a scene in your app, or share with AR Quick Look.

Loading Reality Composer files using generated code

Leverage automatically generated code to load scenes from Xcode.

Loading Reality Composer files manually without generated code

Load Reality Composer files that aren’t part of your Xcode project.

Adding elements to a 3D scene

Add assets to your scene from Reality Composer’s library, or import custom assets.

Arranging elements in a scene

Manipulate objects to complete your Reality Composer scene.

Manipulating Reality Composer scenes from code

Make programmatic changes to your scenes at runtime.

Adding procedural assets to a scene

Create procedurally generated shape primitives to your Reality Composer scene.

Improving the Accessibility of RealityKit Apps

Incorporate assistive technologies in your augmented reality app.

