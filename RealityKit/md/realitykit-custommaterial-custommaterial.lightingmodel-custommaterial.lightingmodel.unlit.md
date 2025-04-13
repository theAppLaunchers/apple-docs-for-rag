

- RealityKit
- CustomMaterial
- CustomMaterial.LightingModel
-  CustomMaterial.LightingModel.unlit 

Case

# CustomMaterial.LightingModel.unlit

The entity renders with no light or shadow calculations.

iOS 15.0+iPadOS 15.0+Mac Catalyst 15.0+macOS 12.0+

``` source
case unlit
```

## Discussion

A custom material that uses the unlit lighting model renders much like an entity with an UnlitMaterial. Custom materials using CustomMaterial.LightingModel.unlit don’t respond to lights in the scene. Use this lighting model for user interface elements or other elements where visibility is more important than fitting in to the environment.

The surface shader for a custom material has access to all of the custom material’s properties as inputs, but only renders based on the value passed to `params.surface().set_emissive_color()`. RealityKit ignores any other property your shader sets on `params.surface().`

## See Also

### Specifying the lighting model

case lit

The entity renders using physically based rendering techniques without a clearcoat.

case clearcoat

The entity renders using physically based rendering techniques with a clearcoat.

