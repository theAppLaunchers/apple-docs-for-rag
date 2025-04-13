

- SwiftUI
- View
-  onPencilSqueeze(perform:) 

Instance Method

# onPencilSqueeze(perform:)

Adds an action to perform when the user squeezes their Apple Pencil.

iOS 17.5+iPadOS 17.5+Mac Catalyst 17.5+macOS 14.5+

``` source
nonisolated
func onPencilSqueeze(perform action: @escaping (PencilSqueezeGesturePhase) -> Void) -> some View
```

## Parameters 

`action`  

The action to perform when the user squeezes their Apple Pencil.

## Return Value

A view that performs `action` when the user squeezes their Apple Pencil.

## Discussion

You should respect people’s setting for the squeeze gesture by reading the preferredPencilSqueezeAction environment value, if the setting makes sense in your app. If it doesn’t, consider giving people a way to specify custom behavior in your app instead.

In the example below, completing an Apple Pencil squeeze gesture will…

- do nothing if this is what the user selected in the Settings app,

- switch the tool to ”Lasso” if this is the action they have configured in the app,

- spill the ink if this is the action they have configured in the app,

- present a custom contextual palette if they haven’t configured a custom action in the app and this is what they selected in the Settings app.

```
enum MyPencilAction: String {
    case spillInk
    ...
}

@Environment(\.preferredPencilSqueezeAction) private var preferredAction
@AppStorage("customPencilSqueezeAction") private var customAction: MyPencilAction?

@State private var contextualPaletteAnchor: PopoverAttachmentAnchor?
@State private var contextualPalettePresented = false

var body: some View {
    MyDrawingCanvas()
        .onPencilSqueeze { phase in
            guard preferredAction != .ignore else {
                // Skip if this is what the user prefers.
                return
            }
            if let customAction {
                // If a custom action is configured, respect it.
                if customAction == .spillInk {
                    switch phase {
                        // Spill the ink while the user is squeezing their Apple Pencil.
                    }
                }
            } else if preferredAction == .showContextualPalette, case let .ended(value) = phase {
                // Present a custom contextual palette if the user prefers it.
                contextualPaletteAnchor = value.hoverPose?.anchor.map { .point($0) }
                contextualPalettePresented = true
            }
        }
        .popover(
            isPresented: $contextualPalettePresented,
            attachmentAnchor: contextualPaletteAnchor ?? .point(.center)
        ) {
            MyContextualPalette()
        }
```

Note

If multiple views with the `onPencilSqueeze` view modifier are visible, all their action closures will be performed when the user squeezes their Apple Pencil.

## See Also

### Recognizing Apple Pencil gestures

func onPencilDoubleTap(perform: (PencilDoubleTapGestureValue) -> Void) -> some View

Adds an action to perform after the user double-taps their Apple Pencil.

var preferredPencilDoubleTapAction: PencilPreferredAction

The action that the user prefers to perform after double-tapping their Apple Pencil, as selected in the Settings app.

var preferredPencilSqueezeAction: PencilPreferredAction

The action that the user prefers to perform when squeezing their Apple Pencil, as selected in the Settings app.

struct PencilPreferredAction

An action that the user prefers to perform after double-tapping their Apple Pencil.

struct PencilDoubleTapGestureValue

Describes the value of an Apple Pencil double-tap gesture.

struct PencilSqueezeGestureValue

Describes the value of an Apple Pencil squeeze gesture.

enum PencilSqueezeGesturePhase

Describes the phase and value of an Apple Pencil squeeze gesture.

struct PencilHoverPose

A value describing the location and distance of an Apple Pencil hovering in the area above a view’s bounds.

