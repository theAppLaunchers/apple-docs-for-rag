

- WebKit
- WKWebView
-  isInspectable 

Instance Property

# isInspectable

A Boolean value that indicates whether you can inspect the view with Safari Web Inspector.

iOS 16.4+iPadOS 16.4+Mac Catalyst 16.4+macOS 13.3+visionOS 1.0+

``` source
@MainActor
var isInspectable: Bool { get set }
```

## Discussion

Defaults to `false`.

Set to `true` at any point in the view’s lifetime to allow Safari Web Inspector access to inspect the view’s content. Then, select your view in Safari’s Develop menu for either your computer or an attached device to inspect it.

If you set this value to `false` during inspection, the system immediately closes Safari Web Inspector and does not provide any further information about the web content.

For more information, see Enabling the Inspection of Web Content in Apps.

