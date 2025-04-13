

- AppKit
- NSBrowserDelegate
-  browser(\_:setObjectValue:forItem:) 

Instance Method

# browser(\_:setObjectValue:forItem:)

Sets the object that the specified item uses to draw its contents to the specified object.

macOS 10.6+

``` source
@MainActor
optional func browser(
    _ browser: NSBrowser,
    setObjectValue object: Any?,
    forItem item: Any?
)
```

## Parameters 

`browser`  

The browser.

`object`  

The object to set.

`item`  

The item whose object is set.

## See Also

### Accessing Components

func browser(NSBrowser, child: Int, ofItem: Any?) -> Any

Asks the delegate to return the child of the specified item at the specified index.

func browser(NSBrowser, isLeafItem: Any?) -> Bool

Asks the delegate whether the specified item is a leaf item (an item that cannot be expanded).

func browser(NSBrowser, shouldEditItem: Any?) -> Bool

Asks the delegate whether the browser may start an editing session for the specified item.

func browser(NSBrowser, objectValueForItem: Any?) -> Any?

Returns the object that the specified item uses to draw its contents.

func rootItem(for: NSBrowser) -> Any?

Asks the delegate to return the root item of the browser.

func browser(NSBrowser, previewViewControllerForLeafItem: Any) -> NSViewController?

Asks the delegate for a controller that provides a preview column for the specified leaf item.

func browser(NSBrowser, headerViewControllerForItem: Any?) -> NSViewController?

Asks the delegate for a controller that provides a header view for the specified column item.

