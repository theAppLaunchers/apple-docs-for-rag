

- RealityKit
- TextureResource
-  init(named:in:) 

Initializer

# init(named:in:)

Asynchronously loads a texture resource from a bundle.

iOS 18.0+iPadOS 18.0+Mac Catalyst 18.0+macOS 15.0+visionOS 1.0+

``` source
@MainActor @preconcurrency
convenience init(
    named name: String,
    in bundle: Bundle? = nil
) async throws
```

## Parameters 

`name`  

The name of the resource. The filename extension is optional.

`bundle`  

The bundle to search for the resource. Use `nil` to indicate the app’s bundle.

## Discussion

RealityKit automatically creates a resource name for the texture resource based on the values of `name` and `bundle`. RealityKit uses the resource name to identify resources, and to match texture resources between networked peers. Specify a unique name for each texture resource you load or generate.

Load textures concurrently with other content for optimal load times without causing your app to hitch.

```
struct SomeRealityView: View {
    var body: some View {
        RealityView { content in
            // Begin loading the texture.
            async let textureA = try? TextureResource(named:"textureA.jpg")
            // Load the scene.
            guard let rootEntity = try? await Entity(named: "SceneA", in: realityKitContentBundle) else {
                return
            }
            // Wait for the texture to finish loading.
            guard let textureA = await textureA else {
                return
            }

            // Create and assign a material that uses the texture to a model entity.
            if let entityA = rootEntity.findEntity(named: "ModelA") as? ModelEntity {
                var material = PhysicallyBasedMaterial()
                material.baseColor = PhysicallyBasedMaterial.BaseColor(tint: .white,
                                                                       texture: .init(textureA))
                entityA.model?.materials[0] = material
            }

            content.add(rootEntity)
        }
    }
}
```

## See Also

### Loading a texture

convenience init(named: String, in: Bundle?, options: TextureResource.CreateOptions) async throws

Asynchronously loads a texture resource from a bundle with options.

convenience init(contentsOf: URL, withName: String?, options: TextureResource.CreateOptions) async throws

Asynchronously creates a texture resource from a file URL with creation options.

convenience init(contentsOf: URL, withName: String?) async throws

Synchronously creates a texture resource from a file URL.

static func load(named: String, in: Bundle?) throws -> TextureResource

Returns a texture resource by synchronously loading it from a bundle.

static func load(named: String, in: Bundle?, options: TextureResource.CreateOptions) throws -> TextureResource

Returns a texture resource by synchronously loading it from a bundle with options.

static func load(contentsOf: URL, withName: String?, options: TextureResource.CreateOptions) throws -> TextureResource

Synchronously loads a texture resource from a URL with options.

static func load(contentsOf: URL, withName: String?) throws -> TextureResource

Synchronously loads a texture resource from a URL.

static func loadAsync(named: String, in: Bundle?) -> LoadRequest&lt;TextureResource>

Returns a load request that creates a texture resource by asynchronously loading it from a bundle.

Deprecated

static func loadAsync(named: String, in: Bundle?, options: TextureResource.CreateOptions) -> LoadRequest&lt;TextureResource>

Returns a load request that creates a texture resource by asynchronously loading it from a bundle with options.

Deprecated

static func loadAsync(contentsOf: URL, withName: String?) -> LoadRequest&lt;TextureResource>

Asynchronously loads a texture resource from a URL.

Deprecated

