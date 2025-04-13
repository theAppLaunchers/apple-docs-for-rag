

- RealityKit
- Materials, textures, and shaders
-  Modifying RealityKit rendering using custom materials 

Article

# Modifying RealityKit rendering using custom materials

Write Metal shader functions to implement custom rendering effects.

## Overview

RealityKit provides several types of materials that render entities using different techniques. Two examples are PhysicallyBasedMaterial, which renders entities in highly realistic fashion, and UnlitMaterial, which renders without any shadow or lighting effects. On iOS 15 and later, CustomMaterial allows you to write shader functions in Metal to modify how RealityKit renders an entity, while still leveraging RealityKit’s built-in shader pipeline.

Note

For the Metal API documentation for custom material shader functions, see the Metal RealityKit APIs PDF.

Custom materials support two types of custom Metal shader functions: *surface shaders* and *geometry modifiers*. Surface shaders are responsible for specifying the final attributes of each pixel that RealityKit draws to render the entity. They also support an optional geometry modifier, which you can use to manipulate the location of the model’s vertices, allowing you to dynamically change the size or shape of the entity.

In shader programming, the term *fragment* refers to a one-pixel portion of an entity. *Fragment shaders* run on the GPU and are responsible for rendering those pixel-size chunks. RealityKit’s built-in fragment shader fires once for every one of the entity’s fragments. In other words, it fires once for every screen pixel potentially affected by rendering that entity. As a result, your surface shader function also fires once for every fragment. RealityKit’s fragment shader calls your surface shader, meaning that surface shaders are also called once for each of the entity’s fragments.

The other type of Metal shader that RealityKit uses is the *vertex shader*. Vertex shaders fire once for every vertex in the entity. If you supply a geometry modifier when creating a custom material, RealityKit’s vertex shader calls it. Geometry modifiers fire once for every vertex in the entity.

For more information on writing Metal shaders, see Debugging the shaders within a draw command or compute dispatch.

### Write a surface shader

To use a custom material, first write a surface shader in Metal. Start by adding a new file to your Xcode project using the Metal File template. You can use any function name you want for your surface shader, but you must prefix your function with the `[[visible]]` keyword. Your function must have no return value and take a single parameter of type `realitykit::surface_parameters`.

The following code listing shows an empty surface shader:

```
#include 
#include 

using namespace metal;

[[visible]]
void myEmptyShader(realitykit::surface_parameters params)
{

}
```

The one parameter that RealityKit passes to your surface shader provides access to all input from the entity’s material, as well as interpolated versions of all of the entity’s per-vertex values, such as UV coordinates and vertex colors. When accessed from a surface shader, Metal returns an interpolated version of per-vertex data, based on the fragment’s position relative to the three vertices that make up its triangle. The following illustration demonstrates how that interpolation works for vertex colors.

Specify output using the various `set_` functions on the parameter’s `surface()` property. For example, to set the base color value for the current fragment, call `params.surface().set_base_color()`. The custom material’s lighting model determines which `set_` functions it supports. Your surface shader must call at least one supported `set_` function or nothing renders. For a list of which `set_` functions each lighting model supports, see lightingModel.

Here are the accessor methods on `realitykit::surface_parameters`, along with what you use them for:

`uniforms()`  
Contains all constant properties, including the current elapsed time and any custom value specified on the CustomMaterial. It also contains matrices for converting values between different coordinate systems, like converting from world space to model space.

`geometry()`  
Contains properties specified on a per-vertex basis, such as a vertex’s position, color, and normal vector. Metal interpolates per-vertex values based on the current fragment’s position relative to the three vertices that make up its triangle.

`textures()`  
Provides access to all of the custom material’s UV-mapped image textures.

`surface()`  
Contains functions to specify and read the fragment’s output values.

The following surface shader calculates and sets the fragment’s base color based on the `tint` and `color` values from the material’s CustomMaterial.BaseColor property.

```
#include 
#include 

using namespace metal;

constexpr sampler textureSampler(address::clamp_to_edge, filter::bicubic);

[[visible]]
void mySurfaceShader(realitykit::surface_parameters params)
{
    // Retrieve the base color tint from the entity's material.
    half3 baseColorTint = (half3)params.material_constants().base_color_tint();

    // Retrieve the entity's texture coordinates.
    float2 uv = params.geometry().uv0();

    // Flip the texture coordinates y-axis. This is only needed for entities
    // loaded from USDZ or .reality files.
    uv.y = 1.0 - uv.y;

    // Sample a value from the material's base color texture based on the 
    // flipped UV coordinates.
    auto tex = params.textures();
    half3 color = (half3)tex.base_color().sample(textureSampler, uv).rgb;

    // Multiply the tint by the sampled value from the texture, and
    // assign the result to the shader's base color property.
    color *= baseColorTint;
    params.surface().set_base_color(color);
}
```

### Write a geometry modifier

If you need to modify the vertex positions or other vertex values for your entity, write a geometry modifier function. Otherwise, you can create your custom material with only a surface shader. To write a geometry modifier, create a new Metal file in your Xcode project, or add a new function to the same file that contains your surface shader.

As with surface shaders, you can name your geometry modifier function anything you want, but you must prefix it with the `[[visible]]` keyword. A geometry shader must have no return value and take a single parameter of type `realitykit::geometry_parameters`.

The following code shows an empty geometry modifier.

```
#include 
#include 
using namespace metal;

[[visible]]
void emptyGeometryModifier(realitykit::geometry_parameters params)
{
}
```

To move vertices before RealityKit renders your entity, call `params.geometry().set_model_position_offset()` or `params.geometry().set_world_position_offset()` with the amount to offset the vertex. Changes made in the geometry modifier only affect how RealityKit renders the model; they don’t affect the original entity in the RealityKit scene. For example, moving a model to a new location in the geometry modifier won’t affect its location for collision detection or other physics calculation.

The following example implements a simple geometry shader that moves every vertex along the z-axis by an amount calculated from the elapsed time.

```
#include 
#include 
using namespace metal;

[[visible]]
void simpleGeometryModifier(realitykit::geometry_parameters params)
{
    float3 zOffset = float3(0.0, 0.0, params.uniforms().time() / 50.0);
    params.geometry().set_world_position_offset(zOffset);
}
```

Important

If your geometry modifier moves any vertices outside of the entity’s bounding box, assign a value to boundsMargin to enlarge the bounding box and prevent RealityKit from incorrectly culling the entity.

### Load the custom shaders

To create a custom material for an entity, first load the Metal library that contains your shader functions, then load the functions by name, as the following sample code demonstrates:

```
// Get the Metal Device.
guard let device = MTLCreateSystemDefaultDevice() else {
    fatalError("Error creating default metal device.")
}

// Get a reference to the Metal library.
let library = device.makeDefaultLibrary()

// Load a geometry modifier function named myGeometryModifier.
let geometryModifier = CustomMaterial.GeometryModifier(named: "myGeometryModifier", 
                                                       in: library)

// Load a surface shader function named mySurfaceShader.
let surfaceShader = CustomMaterial.SurfaceShader(named: "mySurfaceShader", 
                                                 in: library)
```

### Choose a lighting model

Every custom material needs a *lighting model*, which determines the basic approach RealityKit uses to render an entity with a custom material. The lighting model affects how the entity looks and which output functions your surface shader can use. There are three options:

| Lighting Model | Description | Supported Shader Outputs |
|----|----|----|
| `.lit` | Uses physically based rendering (PBR) techniques, but excludes clearcoat rendering. | All except `set_clearcoat()` and `set_clearcoat_roughness()` |
| `.clearcoat` | Uses PBR techniques, including clearcoat. | All |
| `.unlit` | Renders without any shading or lighting calculations. The result is similar to using an UnlitMaterial. | Uses `set_emissive_color()` only |

### Create and use the custom material

In your Swift code, create a custom material using your loaded shader functions and selected lighting model. To create a custom material from scratch, use init(surfaceShader:geometryModifier:lightingModel:), as the following code demonstrates:

```
let customMaterial: CustomMaterial
do {
    try customMaterial = CustomMaterial(surfaceShader: surfaceShader,
                                        geometryModifier: geometryModifier,
                                        lightingModel: .lit)
} catch {
    fatalError(error.localizedDescription)
}

let mesh = MeshResource.generateSphere(radius: 0.5 )
let modelEntity = ModelEntity(mesh: mesh, materials: [customMaterial])
```

Alternatively, you can create a custom material from a model’s existing material. When working with entities loaded from USDZ or `.reality` files, this approach preserves all of the material attributes from the original file. The following code demonstrates loading a model and creating a custom material based on the entity’s existing material:

```
// Load a USDZ from the file system.
guard let robot = try? Entity.load(named: "Robot") else { 
    return 
}

// Make sure the entity has a ModelComponent.
guard var modelComponent = robot.components[ModelComponent.self] else { 
    return 
}

// Loop through the entity's materials and replace the existing material with
// one based on the original material.
guard let customMaterials = try? modelComponent.materials.map({ material -> CustomMaterial in
    let customMaterial = try CustomMaterial(from: material, surfaceShader: surfaceShader)
    return customMaterial
}) else { return}
modelComponent.materials = customMaterials
robot.components[ModelComponent.self] = modelComponent
```

You can download RealityKit’s custom shader Metal API documentation from Custom Shader API.

## See Also

### Shaders

struct ShaderGraphMaterial

typealias FaceCulling

An alias for the cull mode object that’s appropriate for this material class.

typealias TriangleFillMode

An alias for the triangle fill mode object that’s appropriate for this material class.

struct CustomMaterial

A material that works with custom Metal shader functions.

struct SurfaceShader

The custom material’s surface shader function.

struct GeometryModifier

The custom material’s optional shader function that can manipulate an entity’s vertex data.

protocol MaterialFunction

The abstract superclass for objects representing compute functions for RealityKit custom materials .

class Program

An object that represents the backing shader compilation required for custom materials.

struct Descriptor

An object that specifies all parameters necessary to initialize `CustomMaterial` programs

enum CustomShaderStage

