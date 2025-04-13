

- AppKit
- NSTrackingArea
-  init(rect:options:owner:userInfo:) 

Initializer

# init(rect:options:owner:userInfo:)

Initializes and returns an object defining a region of a view to receive mouse-tracking events, mouse-moved events, cursor-update events, or possibly all these events.

macOS 10.5+

``` source
init(
    rect: NSRect,
    options: NSTrackingArea.Options = [],
    owner: Any?,
    userInfo: [AnyHashable : Any]? = nil
)
```

## Parameters 

`rect`  

A rectangle that defines a region of a target view, in the view’s coordinate system, for tracking events related to mouse tracking and cursor updating. The specified rectangle should not exceed the view’s bounds rectangle.

`options`  

One or more constants that specify the type of tracking area, the situations when the area is active, and special behaviors of the tracking area. See the description of NSTrackingArea.Options and related constants for details. You must specify one or more options for the initialized object for the type of tracking area and for when the tracking area is active; zero is not a valid value.

`owner`  

The object to receive the requested mouse-tracking, mouse-moved, or cursor-update messages. It does not necessarily have to be the view associated with the created `NSTrackingArea` object, but should be an object capable of responding to the `NSResponder` methods mouseEntered(with:), mouseExited(with:), mouseMoved(with:), and cursorUpdate(with:).

`userInfo`  

A dictionary containing arbitrary data for each mouse-entered, mouse-exited, and cursor-update event. When handling such an event you can obtain the dictionary by sending userData to the `NSEvent` object. (The dictionary is not available for mouse-moved events.) This parameter may be `nil`.

## Return Value

The newly-initialized tracking area object.

## Discussion

After creating and initializing an `NSTrackingArea` object with this method, you must add it to a target view using the addTrackingArea(_:) method. When changes in the view require changes in the geometry of its tracking areas, the Application Kit invokes updateTrackingAreas(). The view should implement this method to replace the current `NSTrackingArea` object with one with a recomputed area.

### Special Considerations

Beginning with OS X v10.5, the init(rect:options:owner:userInfo:), along with the addTrackingArea(_:) method of `NSView`, replace the `NSView` method addTrackingRect(_:owner:userData:assumeInside:).

## See Also

### Related Documentation

var userInfo: [AnyHashable : Any]?

The dictionary containing the data associated with the receiver when it was created.

var rect: NSRect

The rectangle defining the area encompassed by the receiver.

var owner: AnyObject?

The object owning the receiver, which is the recipient of mouse-tracking, mouse-movement, and cursor-update messages.

var options: NSTrackingArea.Options

The options specified for the receiver.

Cocoa Event Handling Guide

