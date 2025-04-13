

- RealityKit
- CustomMaterial
- CustomMaterial.Opacity
-  init(scale:texture:) 

Initializer

# init(scale:texture:)

Creates an object that defines the opacity of an entity using a single value, a UV-mapped image texture, or both.

iOS 15.0+iPadOS 15.0+Mac Catalyst 15.0+macOS 12.0+

``` source
init(
    scale: Float = 1.0,
    texture: CustomMaterial.Texture? = nil
)
```

## Parameters 

`scale`  

The opacity value for the entire material.

`texture`  

The opacity values as a UV-mapped image.

## Discussion

Both `scale` and `texture` are available to the material’s surface shader function, but RealityKit draws the entity fully opaque unless the surface shader function calls `params.surface().set_opacity()`.

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
        // If the opacity threshold is greater than 0, use masking behavior
        // and set the opacity to either 1.0 or 0.0 depending on the value
        // of the opacity threshold.
        opacity = (opacity 

## See Also

### Creating an opacity object

init(floatLiteral: Float)

Creates an opacity object from a single value.

init(PhysicallyBasedMaterial.Opacity)

Creates an object from the opacity property of an existing physically based material.

