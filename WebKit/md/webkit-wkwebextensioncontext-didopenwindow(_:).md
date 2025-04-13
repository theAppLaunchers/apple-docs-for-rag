

- WebKit
- WKWebExtensionContext
-  didOpenWindow(\_:) 

Instance Method

# didOpenWindow(\_:)

Called by the app when a new window is opened to fire appropriate events with only this extension.

iOS 18.4+iPadOS 18.4+Mac Catalyst 18.4+macOS 15.4+visionOS 2.4+

``` source
@MainActor
func didOpenWindow(_ newWindow: any WKWebExtensionWindow)
```

## Parameters 

`newWindow`  

The newly opened window.

## Discussion

This method informs only the specific extension of the opening of a new window. If the intention is to inform all loaded extensions consistently, you should use the respective method on the extension controller instead.

## See Also

### Related Documentation

func didCloseWindow(any WKWebExtensionWindow)

Called by the app when a window is closed to fire appropriate events with only this extension.

var openWindows: [any WKWebExtensionWindow]

The open windows that are exposed to this extension.

