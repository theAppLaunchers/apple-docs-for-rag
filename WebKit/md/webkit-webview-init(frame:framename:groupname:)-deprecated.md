

- WebKit
- WebView
-  init(frame:frameName:groupName:) Deprecated

Initializer

# init(frame:frameName:groupName:)

Initializes the receiver with a frame rectangle, frame name, and group name.

macOS 10.3–10.14Deprecated

``` source
@MainActor
init!(
    frame: NSRect,
    frameName: String!,
    groupName: String!
)
```

Deprecated

No longer supported; please adopt WKWebView.

## Parameters 

`frame`  

The frame rectangle for the created view object.

`frameName`  

The web frame’s name. This should not be one of the predefined frame names (see the ```` WebFrame```WebFrame/findNamed(_:)`` method for a description of their meaning), but a custom name or a name used in HTML source. This parameter can be  ````nil\`.

`groupName`  

An arbitrary identifier used to group related frames. For example, JavaScript running in a frame can access any other frame in the same group. It’s up to the application how it chooses to scope related frames. This parameter can be `nil`.

## Return Value

An initialized view object or `nil` if the object couldn’t be created.

## Discussion

This method is the designated initializer for the `WebView` class.

