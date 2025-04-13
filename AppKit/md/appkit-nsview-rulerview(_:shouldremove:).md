

- AppKit
- NSView
-  rulerView(\_:shouldRemove:) 

Instance Method

# rulerView(\_:shouldRemove:)

Requests permission for `aRulerView` to remove `aMarker`.

macOS

``` source
@MainActor
func rulerView(
    _ ruler: NSRulerView,
    shouldRemove marker: NSRulerMarker
) -> Bool
```

## Discussion

If the client returns true the ruler view allows the user to remove the marker; if the client returns false the marker is kept pinned to the ruler’s baseline. This message is sent as many times as needed while the user drags the marker.

The user’s ability to remove a marker is typically set on the marker itself, using NSRulerMarker’s isRemovable method. You should use this client view method only when the marker’s removability can vary while the user drags it (for example, if the user must press the Shift key to remove a marker).

## See Also

### Synchronizing with Ruler Views

func rulerView(NSRulerView, didAdd: NSRulerMarker)

Informs the client that `aRulerView` allowed the user to add `aMarker`.

func rulerView(NSRulerView, didMove: NSRulerMarker)

Informs the client that `aRulerView` allowed the user to move `aMarker`.

func rulerView(NSRulerView, didRemove: NSRulerMarker)

Informs the client that `aRulerView` allowed the user to remove `aMarker`.

func rulerView(NSRulerView, handleMouseDownWith: NSEvent)

Informs the client that the user has pressed the mouse button while the cursor is in the ruler area of `aRulerView`.

func rulerView(NSRulerView, locationFor: NSPoint) -> CGFloat

func rulerView(NSRulerView, pointForLocation: CGFloat) -> NSPoint

func rulerView(NSRulerView, shouldAdd: NSRulerMarker) -> Bool

Requests permission for `aRulerView` to add `aMarker`, an NSRulerMarker being dragged onto the ruler by the user.

func rulerView(NSRulerView, shouldMove: NSRulerMarker) -> Bool

Requests permission for `aRulerView` to move `aMarker`.

func rulerView(NSRulerView, willAdd: NSRulerMarker, atLocation: CGFloat) -> CGFloat

Informs the client that `aRulerView` will add the new NSRulerMarker, `aMarker`.

func rulerView(NSRulerView, willMove: NSRulerMarker, toLocation: CGFloat) -> CGFloat

Informs the client that `aRulerView` will move `aMarker`, an NSRulerMarker already on the ruler view.

func rulerView(NSRulerView, willSetClientView: NSView)

Informs the client view that `aRulerView` is about to be appropriated by `newClient`.

