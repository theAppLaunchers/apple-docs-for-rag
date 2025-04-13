

- SwiftUI
- View
-  onVolumeViewpointChange(updateStrategy:initial:\_:) 

Instance Method

# onVolumeViewpointChange(updateStrategy:initial:\_:)

Adds an action to perform when the viewpoint of the volume changes.

visionOS 2.0+

``` source
@MainActor @preconcurrency
func onVolumeViewpointChange(
    updateStrategy: VolumeViewpointUpdateStrategy = .supported,
    initial: Bool = true,
    _ action: @escaping (Viewpoint3D, Viewpoint3D) -> Void
) -> some View
```

## Parameters 

`updateStrategy`  

Whether the action should be run for all viewpoint changes or only for supported viewpoint changes.

`initial`  

Whether the action should be run when this view initially appears.

`action`  

A closure to run when the viewpoint changes. The closure is also run when the volume is first opened.

## Discussion

Use the provided Viewpoint3D to update the content of the volume:

```
struct RobotContentView: View {
    @State var robotRotation: Rotation3D = .identity

    var body: some View {
        Model3D(named: "robot")
            .onVolumeViewpointChange { _, newValue in
                robotRotation = Rotation3D.slerp(
                    from: robotRotation,
                    to: newValue.squareAzimuth.orientation,
                    t: 1.0,
                    along: .shortest
                )
            }
            .rotation3DEffect(robotRotation)
            .animation(.easeInOut, value: robotRotation)
    }
}
```

By default, the action will only be run when the new viewpoint is equivalent to one of the values provided through supportedVolumeViewpoints(_:). The viewpoint will be equivalent to where the window bar and ornaments are presented for a volume. Providing `.all` for the `updateStrategy` argument will result in the action being called without regard to the supported viewpoints.

To determine if the volume is being viewed from an unsupported viewpoint, provide `.all` for the `updateStrategy` argument and check if the viewpoint is not within the supported viewpoints:

```
struct ContentView: View {
    @State var showingMoveToFrontSign = false
    @State var moveToFrontSignViewpoint: Viewpoint3D = .standard

    let supportedViewpoints = [SquareAzimuth.front]

    var body: some View {
        MoveToFrontSignView(viewpoint: moveToFrontSignViewpoint)
            .opacity(showingMoveToFrontSign ? 1.0 : 0.0)
            .animation(.easeInOut, value: showingMoveToFrontSign)
            .onVolumeViewpointChange(updateStrategy: .all)
                { _, newValue in

                moveToFrontSignViewpoint = newViewpoint

                let isSupported = supportedViewpoints.contains(
                    newViewpoint.squareAzimuth)
                showingMoveToFrontSign = !isSupported
            }
            .supportedVolumeViewpoints(supportedViewpoints)
    }
}
```

The old and new Viewpoint3D provided to the action are relative to the center of the volume.

Reading this value is only valid inside a View that inherits the environment of a Scene created with a VolumetricWindowStyle. This value will be equivalent to standard when read within a standard window.

## See Also

### Interacting with volumes

func supportedVolumeViewpoints(SquareAzimuth.Set) -> some View

Specifies which viewpoints are supported for the window bar and ornaments in a volume.

struct VolumeViewpointUpdateStrategy

A type describing when the action provided to onVolumeViewpointChange(updateStrategy:initial:_:) should be called.

struct Viewpoint3D

A type describing what direction something is being viewed from.

enum SquareAzimuth

A type describing what direction something is being viewed from along the horizontal plane and snapped to 4 directions.

struct WorldAlignmentBehavior

A type representing the world alignment behavior for a scene.

func volumeWorldAlignment(WorldAlignmentBehavior) -> some Scene

Specifies how a volume should be aligned when moved in the world.

struct WorldScalingBehavior

Specifies the scaling behavior a window should have within the world.

func defaultWorldScaling(WorldScalingBehavior) -> some Scene

Specify the world scaling behavior for the window.

struct WorldScalingCompensation

Indicates whether returned metrics will take dynamic scaling into account.

var worldTrackingLimitations: Set&lt;WorldTrackingLimitation>

The current limitations of the device tracking the user’s surroundings.

struct WorldTrackingLimitation

A structure to represent limitations of tracking the user’s surroundings.

