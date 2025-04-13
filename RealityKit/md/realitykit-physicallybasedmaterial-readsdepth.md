

- RealityKit
- PhysicallyBasedMaterial
-  readsDepth 

Instance Property

# readsDepth

A boolean value that determines whether this material performs the depth test by reading RealityKit’s depth buffer.

iOS 18.0+iPadOS 18.0+Mac Catalyst 18.0+macOS 15.0+visionOS 2.0+

``` source
var readsDepth: Bool { get set }
```

## Discussion

If true, meshes with this material will depth test each of their fragments when being rendered. If an object that writes depth is in front of this material, this material will be hidden.

If false, meshes with this material will ignore the depth test, and always render all of their fragments during their draw call, regardless of the positioning of other objects in the scene. Note that other objects may still render on top of this material, depending on draw order.

The default value is true.

## See Also

### Setting depth testing properties

var writesDepth: Bool

A boolean value that determines whether this material writes its depth into RealityKit’s depth buffer.

