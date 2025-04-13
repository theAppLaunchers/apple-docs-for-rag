

- AppKit
- NSWindowDelegate
-  window(\_:willPositionSheet:using:) 

Instance Method

# window(\_:willPositionSheet:using:)

Tells the delegate that the window is about to show a sheet at the specified location, giving it the opportunity to return a custom location for the attachment of the sheet to the window.

macOS

``` source
@MainActor
optional func window(
    _ window: NSWindow,
    willPositionSheet sheet: NSWindow,
    using rect: NSRect
) -> NSRect
```

## Parameters 

`window`  

The window containing the sheet to be animated.

`sheet`  

The sheet to be shown.

`rect`  

The default sheet location, just under the title bar of the window, aligned with the left and right edges of the window.

## Return Value

The custom location specified.

## Discussion

This method is also called whenever the user resizes `window` while `sheet` is attached.

This method is useful in many situations. If your window has a toolbar, for example, you can specify a location for the sheet that is just below it. If you want the sheet associated with a certain control or view, you could position the sheet so that it appears to originate from the object (through animation) or is positioned next to it.

Neither the `rect` parameter nor the returned `NSRect` value define the boundary of the sheet. They indicate where the top-left edge of the sheet is attached to the window. The origin is expressed in window coordinates; the default `origin.y` value is the height of the content view and the default `origin.x` value is 0. The `size.width` value indicates the width and behavior of the initial animation; if `size.width` is narrower than the sheet, the sheet genies out from the specified location, and if `size.width` is wider than the sheet, the sheet slides out. You cannot affect the size of the sheet through the `size.width` and `size.height` fields. It is recommended that you specify zero for the `size.height` value as this field may have additional meaning in a future release.

## See Also

### Related Documentation

Window Programming Guide

### Managing Sheets

func windowWillBeginSheet(Notification)

Notifies the delegate that the window is about to open a sheet.

func windowDidEndSheet(Notification)

Tells the delegate that the window has closed a sheet.

