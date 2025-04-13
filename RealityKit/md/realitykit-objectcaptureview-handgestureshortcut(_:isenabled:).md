

- RealityKit
- ObjectCaptureView
-  handGestureShortcut(\_:isEnabled:) 

Instance Method

# handGestureShortcut(\_:isEnabled:)

Assigns a hand gesture shortcut to the modified control.

RealityKitSwiftUIiOS 18.0+iPadOS 18.0+macOS 15.0+tvOS 18.0+watchOS 11.0+

``` source
nonisolated
func handGestureShortcut(
    _ shortcut: HandGestureShortcut,
    isEnabled: Bool = true
) -> some View
```

## Parameters 

`shortcut`  

The shortcut to associate with this control.

`isEnabled`  

A Boolean value that indicates whether the shortcut is is enabled for this control.

## Discussion

Performing the control’s shortcut while the control is anywhere in the frontmost scene is equivalent to direct interaction with the control to perform its primary action.

The following example lets users of a watchOS music app toggle playback by double-tapping their thumb and index finger together:

```
struct PlaybackControls: View {
    let model: TrackModel

    var body: some View {
        HStack {
            Button("Skip Back") {
                model.skipBack()
            }

            Button("Play/Pause") {
                model.playPause()
            }
            .handGestureShortcut(.primaryAction)

            Button("Skip Forward") {
                model.skipForward()
            }
        }
    }
}
```

The target of a hand gesture shortcut is resolved in a leading-to-trailing traversal of the active scene.

