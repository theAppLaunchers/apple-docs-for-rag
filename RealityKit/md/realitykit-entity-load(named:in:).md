

- RealityKit
- Entity
-  load(named:in:) 

Type Method

# load(named:in:)

Returns an entity by synchronously loading it from a bundle.

iOS 13.0+iPadOS 13.0+Mac Catalyst 13.0+macOS 10.15+visionOS

``` source
@MainActor @preconcurrency
static func load(
    named name: String,
    in bundle: Bundle? = nil
) throws -> Entity
```

## Parameters 

`name`  

The base name of the file to load. An extension isn’t required, but you can provide one to resolve collisions. In the presence of a collision, the provided name resolves with the following order of precedence: \[`.usdz`, `.usd`, `.usdc`, `.usda`\].

`bundle`  

The bundle containing the file. Use `nil` to search the app’s main bundle.

## Return Value

The root entity in the loaded file.

## Mentioned in 

Loading remote assets in multiplayer apps

## Discussion

Loading an Entity with this method blocks the main actor because it’s synchronous, so only call it from a command-line application. The method can stall a regular app, which makes it visibly hitch, and the system terminates an app if its UI becomes unresponsive. See init(named:in:) for an example that demonstrates how to safely load content.

RealityKit supports loading entities from USD (`.usd`, `.usda`, `.usdc`, `.usdz`) and Reality (`.reality`) files.

When building your app, Xcode automatically converts any Reality Composer projects (`.rcproject`) in the selected target into Reality files, which it then copies into your app’s bundle.

For more information on loading entities, see Loading entities from a file.

## See Also

### Loading an entity hierarchy

static func load(contentsOf: URL, withName: String?) throws -> Entity

Returns an entity by synchronously loading it from a file URL.

static func loadAsync(named: String, in: Bundle?) -> LoadRequest&lt;Entity>

Returns a load request that creates an entity by asynchronously loading it from a bundle.

Deprecated

static func loadAsync(contentsOf: URL, withName: String?) -> LoadRequest&lt;Entity>

Returns a load request that creates an entity by asynchronously loading it from a file URL and preserving the entity’s hierarchy.

Deprecated

