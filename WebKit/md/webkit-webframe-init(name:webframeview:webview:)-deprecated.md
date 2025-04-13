

- WebKit
- WebFrame
-  init(name:webFrameView:webView:) Deprecated

Initializer

# init(name:webFrameView:webView:)

Initializes the receiver with a frame name, web frame view, and controlling web view.

macOS 10.3–10.14Deprecated

``` source
init!(
    name: String!,
    webFrameView view: WebFrameView!,
    webView: WebView!
)
```

## Parameters 

`name`  

The frame name. Typically a custom name or `nil` (if none is specified). It would be inappropriate to use one of the predefined frame names described in findNamed(_:) as they have special meanings.

`view`  

The view that displays this web frame—the view associated with the receiver.

`webView`  

The parent view that manages the main frame and its children.

## Return Value

An initialized web frame.

## Discussion

Normally, you do not invoke this method directly. `WebView` objects automatically create the main frame and subsequent children when new content is loaded. Send a load(_:) message to the main frame of a `WebView` to load web content.

This method is the designated initializer for the `WebFrame` class.

