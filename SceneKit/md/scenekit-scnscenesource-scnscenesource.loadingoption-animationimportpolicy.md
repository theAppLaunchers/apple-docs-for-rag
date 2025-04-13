

- SceneKit
- SCNSceneSource
- SCNSceneSource.LoadingOption
-  animationImportPolicy 

Type Property

# animationImportPolicy

An option for controlling the playback of animations in a scene file.

iOSiPadOSMac Catalyst 13.1+macOS 10.10+tvOSvisionOSwatchOS

``` source
static let animationImportPolicy: SCNSceneSource.LoadingOption
```

## Discussion

The value for this key is one of the constants listed in `Animation Import Policies`.

The default value for this key is playRepeatedly. For apps built for 10.9 or earlier, the default value is playUsingSceneTimeBase.

## See Also

### Type Properties

struct AnimationImportPolicy

Options for playing animations loaded from a scene file, used with the animationImportPolicy key in options dictionaries.

static let assetDirectoryURLs: SCNSceneSource.LoadingOption

Locations to use for resolving relative URLs to external resources.

static let checkConsistency: SCNSceneSource.LoadingOption

An option to validate scene files while loading.

static let convertToYUp: SCNSceneSource.LoadingOption

An option for whether to transform assets loaded from the scene file for use in a coordinate system where the y-axis points up.

static let convertUnitsToMeters: SCNSceneSource.LoadingOption

An option for whether to automatically scale the scene’s contents.

static let createNormalsIfAbsent: SCNSceneSource.LoadingOption

An option for automatically generating surface normals if they are absent when loading geometry.

static let flattenScene: SCNSceneSource.LoadingOption

An option for automatically merging portions of a scene graph during loading.

static let overrideAssetURLs: SCNSceneSource.LoadingOption

An option to attempt loading external resources using their URLs as specified in a scene file.

static let preserveOriginalTopology: SCNSceneSource.LoadingOption

static let strictConformance: SCNSceneSource.LoadingOption

An option to interpret scene files exactly as specified by the scene file format.

static let useSafeMode: SCNSceneSource.LoadingOption

An option to limit filesystem and network access for external resources referenced by a scene file.

Deprecated

