

- RealityKit
- EnvironmentResource
-  init(cube:options:) 

Initializer

# init(cube:options:)

Asynchronously creates an environment resource from a cube texture.

iOS 18.0+iPadOS 18.0+Mac Catalyst 18.0+macOS 15.0+visionOS 2.0+

``` source
@MainActor @preconcurrency
convenience init(
    cube cubeTexture: TextureResource,
    options: EnvironmentResource.CreateOptions
) async throws
```

## Parameters 

`cubeTexture`  

A skybox cube texture of type `.cubeType` with `.color` or `.hdrColor` semantics.

`options`  

A configuration for generating the environment resource.

## Discussion

RealityKit generates an environment resource from a skybox cube texture of the environment. The created environment shares the input skybox.

Note

EnvironmentResource.CreateOptions.SamplingQuality.high and EnvironmentResource.CreateOptions.SamplingQuality.veryHigh, along with astc(blockSize:quality:) compression options, are only available in macOS. Use these options to write optimized scenes for all target platforms when exporting from macOS with write(to:). Compression options also significantly reduce an environmental resource’s memory and disk usage.

```
// Use compression and high quality options to export optimized resources.
let cube = try TextureResource(
    cubeFromEquirectangular: image,
    quality: .high,
    options: TextureResource.CreateOptions(semantic: .color)
)

let options = EnvironmentResource.CreateOptions(
    samplingQuality: .high,
    specularCubeDimension: cube.width/2,
    compression: .astc(blockSize: .block4x4, quality: .high)
)

let environment = try EnvironmentResource(
    cube: cube,
    options: EnvironmentResource.CreateOptions(
        samplingQuality: .high,
        specularCubeDimension: cube.width/2,
        compression: .astc(blockSize: .block4x4, quality: .high)
    )
)

let lightEntity = Entity()
lightEntity.components.set(ImageBasedLightComponent(
    source: .single(environment)
))
...
```

Note

If you request `.astc` compression and `cubeTexture` isn’t already compressed, RealityKit compresses it.

## See Also

### Loading the resource

convenience init(named: String, in: Bundle?) async throws

Asynchronously loads an environment resource from a bundle.

convenience init(equirectangular: CGImage, withName: String?) throws

Synchronously creates an environment resource from an equirectangular image.

convenience init(equirectangular: CGImage, withName: String?) async throws

Asynchronously generates an environment resource from an equirectangular image.

convenience init(cube: TextureResource, options: EnvironmentResource.CreateOptions) throws

Synchronously generates an environment resource from a cube texture resource.

static func load(named: String, in: Bundle?) throws -> EnvironmentResource

Synchronously loads an environment resource from a bundle.

