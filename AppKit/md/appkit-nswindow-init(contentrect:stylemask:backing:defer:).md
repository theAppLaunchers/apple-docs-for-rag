

- AppKit
- NSWindow
-  init(contentRect:styleMask:backing:defer:) 

Initializer

# init(contentRect:styleMask:backing:defer:)

Initializes the window with the specified values.

macOS

``` source
@MainActor
init(
    contentRect: NSRect,
    styleMask style: NSWindow.StyleMask,
    backing backingStoreType: NSWindow.BackingStoreType,
    defer flag: Bool
)
```

## Parameters 

`contentRect`  

Origin and size of the window’s content area in screen coordinates. Note that the window server limits window position coordinates to ±16,000 and sizes to 10,000.

`style`  

The window’s style. It can be `NSBorderlessWindowMask`, or it can contain any of the options described in NSWindow.StyleMask, combined using the C bitwise OR operator. Borderless windows display none of the usual peripheral elements and are generally useful only for display or caching purposes; you should normally not need to create them. Also, note that a window’s style mask should include `NSTitledWindowMask` if it includes any of the others.

`backingStoreType`  

Specifies how the drawing done in the window is buffered by the window device, and possible values are described in NSWindow.BackingStoreType.

`flag`  

Specifies whether the window server creates a window device for the window immediately. When true, the window server defers creating the window device until the window is moved onscreen. All display messages sent to the window or its views are postponed until the window is created, just before it’s moved onscreen.

## Return Value

The initialized window.

## Discussion

This method is the designated initializer for the `NSWindow` class.

Deferring the creation of the window improves launch time and minimizes the virtual memory load on the window server.

The new window creates a view to be its default content view. You can replace it with your own object by setting the contentView property.

## See Also

### Related Documentation

var isOneShot: Bool

A Boolean value that indicates whether the window device the window manages is freed when it’s removed from the screen list.

Deprecated

func orderFront(Any?)

Moves the window to the front of its level in the screen list, without changing either the key window or the main window.

class NSWindow

A window that an app displays on the screen.

### Creating a Window

convenience init(contentViewController: NSViewController)

Creates a titled window that contains the specified content view controller.

convenience init(contentRect: NSRect, styleMask: NSWindow.StyleMask, backing: NSWindow.BackingStoreType, defer: Bool, screen: NSScreen?)

Initializes an allocated window with the specified values.

