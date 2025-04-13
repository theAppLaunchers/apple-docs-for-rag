

- RealityKit
- CustomMaterial
- CustomMaterial.Opacity
-  init(\_:) 

Initializer

# init(\_:)

Creates an object from the opacity property of an existing physically based material.

iOS 15.0+iPadOS 15.0+Mac Catalyst 15.0+macOS 12.0+

``` source
init(_ value: PhysicallyBasedMaterial.Opacity)
```

## Parameters 

`value`  

The opacity property from the PhysicallyBasedMaterial’s blending property.

## Discussion

This initializer creates a new object by copying values from an existing physically based material’s blending property. All of the copied values, including scale, texture, and opacityThreshold are available to the material’s surface shader function, but RealityKit draws the entity fully opaque unless the surface shader function calls `params.surface().set_opacity()`.

The following Metal code demonstrates how to emulate the blending logic RealityKit uses to render entities with a PhysicallyBasedMaterial in your custom material’s surface shader function:

```
    // Retrieve the opacity scale and threshold from the CustomMaterial.
    float opacityScale = params.material_constants().opacity_scale();
    float opacityThreshold = params.material_constants().opacity_threshold();

    // Retrieve the entity's texture coordinates.
    float2 uv = params.geometry().uv0();

    // Entities loaded from USDZ or .reality files use texture coordinates with
    // a flipped y-axis. This compensates for that.
    uv.y = 1.0 - uv.y;

    // Retrieve the opacity texture from the material.
    auto tex = params.textures();

    // Sample the value from the opacity texture.
    half opacity = tex.opacity().sample(textureSampler, uv).r;

    if (opacityThreshold > 0.0) {
        // If the opacity threshold is greater than 0, use masking
        // behavior and set the opacity to either 1.0 or 0.0 depending
        // on the value of the opacity threshold.
        opacity = (opacity 

## See Also

### Creating an opacity object

init(floatLiteral: Float)

Creates an opacity object from a single value.

init(scale: Float, texture: CustomMaterial.Texture?)

Creates an object that defines the opacity of an entity using a single value, a UV-mapped image texture, or both.

