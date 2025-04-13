

- SwiftUI
- EnvironmentValues
-  immersiveSpaceDisplacement 

Instance Property

# immersiveSpaceDisplacement

The displacement that the system applies to the immersive space when moving the space away from its default position, in meters.

visionOS 1.1+

``` source
var immersiveSpaceDisplacement: Pose3D { get }
```

## Discussion

By default, the system places the origin of the immersive space at floor level, at the person’s feet. When joining a shared activity, the system moves the immersive space to an appropriate location for all participants. As participants join and leave the activity, the location of participants and the immersive space can update. Read this property to get the current offset of the immersive space relative to its default position.

If you access this property outside of an open immersive space, it contains the value identity.

If you display participant-specific views or entities in your shared activity, use the inverse of this displacement value to position those views and entities in the immersive space. Applying the inverse value positions them as if they were in a single-participant immersive space.

In the following example, this value is applied to position a game HUD entity at the person’s location, rather than the shared activity’s location:

```
@main
struct GameApp: App {
    var body: some Scene {
        ImmersiveSpace {
            ImmersiveGameView()
        }
    }
}

struct ImmersiveGameView: View {
    @Environment(\.immersiveSpaceDisplacement) private var immersiveSpaceDisplacement

    let gameHUDEntity = makeGameHUDEntity()

    var body: some View {
        RealityView { content in
            // ...
        } update: { content in
            let inverseDisplacement = float4x4(immersiveSpaceDisplacement.inverse)
            gameHUDEntity.setTransformMatrix(inverseDisplacement, relativeTo: nil)
        }
    }
}
```

## See Also

### Creating an immersive space

struct ImmersiveSpace

A scene that presents its content in an unbounded space.

struct ImmersiveSpaceContentBuilder

A result builder for composing a collection of immersive space elements.

func immersionStyle(selection: Binding&lt;any ImmersionStyle>, in: any ImmersionStyle...) -> some Scene

Sets the style for an immersive space.

protocol ImmersionStyle

The styles that an immersive space can have.

