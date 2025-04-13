

- AppKit
- NSView
-  acceptsFirstMouse(for:) 

Instance Method

# acceptsFirstMouse(for:)

Overridden by subclasses to return true if the view should be sent a mouseDown(with:) message for an initial mouse-down event, false if not.

macOS

``` source
@MainActor
func acceptsFirstMouse(for event: NSEvent?) -> Bool
```

## Parameters 

`event`  

The initial mouse-down event, which must be over the view in its window.

## Discussion

The view can either return a value unconditionally or use the location of `theEvent` to determine whether or not it wants the event. The default implementation ignores `theEvent` and returns false.

Override this method in a subclass to allow instances to respond to click-through. This allows the user to click on a view in an inactive window, activating the view with one click, instead of clicking first to make the window active and then clicking the view. Most view objects refuse a click-through attempt, so the event simply activates the window. Many control objects, however, such as instances of NSButton and NSSlider, do accept them, so the user can immediately manipulate the control without having to release the mouse button.

## See Also

### Handling Events in the View

func hitTest(NSPoint) -> NSView?

Returns the farthest descendant of the view in the view hierarchy (including itself) that contains a specified point, or `nil` if that point lies completely outside the view.

func isMousePoint(NSPoint, in: NSRect) -> Bool

Returns whether a region of the view contains a specified point, accounting for whether the view is flipped or not.

func performKeyEquivalent(with: NSEvent) -> Bool

Implemented by subclasses to respond to key equivalents (also known as keyboard shortcuts).

func rightMouseDown(with: NSEvent)

Informs the receiver that the user has pressed the right mouse button.

var mouseDownCanMoveWindow: Bool

A Boolean value indicating whether the view can pass mouse down events through to its superviews.

var inputContext: NSTextInputContext?

The text input context object for the view.

