

- RealityKit
- CustomMaterial
- CustomMaterial.AmbientOcclusion
-  init(texture:) 

Initializer

# init(texture:)

Creates an object from an image texture.

iOS 15.0+iPadOS 15.0+Mac Catalyst 15.0+macOS 12.0+

``` source
init(texture: CustomMaterial.Texture? = nil)
```

## Parameters 

`texture`  

A UV-mapped image texture that defines the entity’s exposure to ambient light.

## Discussion

Ambient occlusion represents the entity’s exposure to ambient light. This function creates a new ambient occlusion object from a UV-mapped image texture.

Specify ambient occlusion by using a UV-mapped image called an *ambient occlusion map*. A value of black (`0.0`) represents parts of the model that receive less ambient light because that part of the model is a crevice, dent, or recessed area, or because another part of the same entity is preventing ambient light from reaching it. Ambient occlusion values of white (`1.0`) represent flat portions of the model that receive full ambient light. You generate ambient occlusion maps by using a 3D software package.

The ambient occlusion texture is available in the material’s surface shader, but RealityKit doesn’t render ambient occlusion unless the surface shader calls `params.surface().set_ambient_occlusion()`.

The following Metal code shows how to use the ambient occlusion texture in a surface shader function:

```
    // Retrieve the entity's texture coordinates.
    float2 uv = params.geometry().uv0();

    // Entities loaded from USDZ or .reality files have texture coordinates
    // with a flipped y-axis. This adjusts for that.
    uv.y = 1.0 - uv.y;

    // Sample the ambient occlusion texture and use it to set the
    // ambient occlusion value to use during rendering.
    auto tex = params.textures();
    half metallic = tex.ambient_occlusion().sample(textureSampler, uv).r;
    params.surface().set_ambient_occlusion(metallic);
```

## See Also

### Creating an ambient occlusion object

init(PhysicallyBasedMaterial.AmbientOcclusion)

Creates an object from a physically based material’s ambient occlusion property.

