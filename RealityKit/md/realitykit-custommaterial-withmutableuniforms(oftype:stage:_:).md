

- RealityKit
- CustomMaterial
-  withMutableUniforms(ofType:stage:\_:) 

Instance Method

# withMutableUniforms(ofType:stage:\_:)

Calls the given closure with an inout reference to the underlying storage bound to the custom uniforms argument of a surface shader or geometry modifier.

iOS 18.0+iPadOS 18.0+Mac Catalyst 18.0+macOS 15.0+

``` source
mutating func withMutableUniforms(
    ofType: UniformsType.Type,
    stage: CustomShaderStage,
    _ callback: (inout UniformsType, inout CustomMaterial.ResourceStorage) -> Void
)
```

## Discussion

SurfaceShaders and GeometryModifiers can declare an argument buffer parameter to be passed into their shader, along with the normal built in PBR parameters. This vastly increases the amount of data your surface shader or geometry modifier can have access to.

To use this feature, declare a custom uniforms struct in a header shared by your metal and swift code.

```
 // Texture types do not bridge to Swift,
 // so some preprocessing work is necessary.
 #ifdef __METAL_VERSION__
 #define TEXTURE_2D metal::texture2d
 #else
 #define TEXTURE_2D uint64_t
 #endif

 typedef struct {
    TEXTURE_2D noiseTexture;
    float2 noiseUVOffset;
 } SurfaceCustomUniforms;

 typedef struct {
    float vertexAnimationSpeed;
    float vertexAnimationAmplitude;
 } GeometryCustomUniforms;
```

Next, define your material functions in metal and pass the argument buffer you defined in a shared header as a second argument. Note to use this feature your material function must be `[[stitchable]]`, instead of `[[visible]]` as well.

```
#include 
#include 
#include "SharedHeader.h"

constexpr sampler kSampler(coord::normalized,
                           address::repeat,
                           filter::linear);

[[stitchable]]
void surfaceShaderWithCustomUniforms(realitykit::surface_parameters params,
                                      constant SurfaceCustomUniforms &customParams)
{
    float2 uv = params.geometry().uv0();

    half4 noiseSample = customParams.noiseTexture.sample(kSampler, uv + customParams.noiseUVOffset);
    half4 baseColorSample = params.textures().base_color().sample(kSampler, uv);

    params.surface().set_base_color(baseColorSample.rgb + noiseSample.rgb);
}

[[stitchable]]
void geometryModifierWithCustomUniforms(realitykit::geometry_parameters params,
                                        constant GeometryCustomUniforms &customParams)
{
    float currentTime = params.uniforms().time() * customParams.vertexAnimationSpeed;
    params.geometry().set_model_position_offset(sin(currentTime) * customParams.vertexAnimationAmplitude * params.geometry().normal());
}
```

Finally, modify these custom uniforms in swift by using this method.

```
 var customMaterial = CustomMaterial(surfaceShader: surfaceShader, lightingModel: .lit)
 customMaterial.withMutableUniforms(ofType: SurfaceCustomUniforms.self, stage: .surfaceShader) { params, resources in
    params.noiseUVOffset = SIMD2(x: 0.25, x: 0.25)
    resources[textureResource: \.noiseTexture] = noiseTexture
 }
 customMaterial.withMutableUniforms(ofType: GeometryCustomUniforms.self, stage: .geometryModifier) { params, resources in
    params.vertexAnimationSpeed = 2.0
    params.vertexAnimationAmplitude = 0.1
 }
```

Material Functions support one additional argument buffer parameter like this, per stage.

## See Also

### Setting shader properties

var program: CustomMaterial.Program

var custom: CustomMaterial.Custom

User-defined properties for the material’s shader functions.

var lightingModel: CustomMaterial.LightingModel

The lighting model that the material uses.

func withMutableUniforms&lt;UniformsType>(ofType: UniformsType.Type, (inout UniformsType, inout CustomMaterial.ResourceStorage&lt;UniformsType>) -> Void)

Calls the given closure with an inout reference to the underlying storage bound to the custom uniforms argument of a surface shader and geometry modifier.

