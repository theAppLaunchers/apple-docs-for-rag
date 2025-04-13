

- AppKit
- NSWindow
-  frameRect(forContentRect:styleMask:) 

Type Method

# frameRect(forContentRect:styleMask:)

Returns the frame rectangle used by a window with a given content rectangle and window style.

macOS

``` source
@MainActor
class func frameRect(
    forContentRect cRect: NSRect,
    styleMask style: NSWindow.StyleMask
) -> NSRect
```

## Parameters 

`cRect`  

The content rectangle for a window expressed in screen coordinates.

`style`  

The window style for the window. See NSWindow.StyleMask for a list of style mask values.

## Return Value

The frame rectangle, expressed in screen coordinates, used by the window with `cRect` and `style`.

## Discussion

When a `NSWindow` instance is available, you should use frameRect(forContentRect:) instead of this method.

## See Also

### Getting Layout Information

class func contentRect(forFrameRect: NSRect, styleMask: NSWindow.StyleMask) -> NSRect

Returns the content rectangle used by a window with a given frame rectangle and window style.

class func minFrameWidth(withTitle: String, styleMask: NSWindow.StyleMask) -> CGFloat

Returns the minimum width a window’s frame rectangle must have for it to display a title, with a given window style.

func contentRect(forFrameRect: NSRect) -> NSRect

Returns the window’s content rectangle with a given frame rectangle.

func frameRect(forContentRect: NSRect) -> NSRect

Returns the window’s frame rectangle with a given content rectangle.

