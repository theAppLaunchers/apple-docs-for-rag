

- RealityKit
- CustomMaterial
- CustomMaterial.GeometryModifier
-  init(named:in:) 

Initializer

# init(named:in:)

Creates a geometry modifier object from a named function in a Metal library.

iOS 15.0+iPadOS 15.0+Mac Catalyst 15.0+macOS 12.0+

``` source
init(
    named name: String,
    in library: any MTLLibrary
)
```

## Parameters 

`name`  

The name of the geometry modifier function.

`library`  

The Metal library that contains the function.

## Discussion

To create a geometry modifier function for a custom material, create a Metal file in your Xcode project. Prefix the function with the keyword `[[visible]]`. The function needs to take a single parameter of type `realitykit::geometry_parameters`.

Here’s what a minimal geometry modifier function looks like:

```
#include 
#include 
using namespace metal;

[[visible]] void myGeometryModifier(realitykit::geometry_parameters
params) {
    // Use params.geometry().set_model_position_offset() to move the vertex.
}
```

To create a custom material using this shader, get a reference to your app’s Metal library. You can do that like this:

```
guard let device = MTLCreateSystemDefaultDevice() else {
    fatalError("Error creating default metal device.")
}
guard let library = maybeDevice.makeDefaultLibrary() else {
    fatalError("Error creating default metal library")
}
```

Once you’ve got a reference to your Metal library, use it to create the surface shader reference like this:

```
let geometryModifier = CustomMaterial.GeometryModifier(
    named: "myGeometryModifier",
    in: library
)
```

Important

RealityKit loads surface shader functions by name, so the name of your surface shader function needs to be unique and exactly match the `name` parameter.

For more information on creating custom materials and writing shader functions, see Modifying RealityKit rendering using custom materials.

