

- RealityKit
- ARView
-  audioListener 

Instance Property

# audioListener

The entity that defines the listener position and orientation for spatial audio.

iOS 13.0+iPadOS 13.0+Mac Catalyst 13.0+macOS 10.15+

``` source
@MainActor @preconcurrency
var audioListener: Entity? { get set }
```

## Discussion

Set the audioListener to the entity in the scene from whose point of view RealityKit should render spatial audio.

By default, the property is set to `nil`, in which case the active camera acts as the audio listener. This is usually what you want, because the camera typically mirrors the user’s point of view.

## See Also

### Providing environmental context

var environment: ARView.Environment

The view’s background, lighting, and acoustic properties.

var physicsOrigin: Entity?

The entity that defines the origin of the scene’s physics simulation.

