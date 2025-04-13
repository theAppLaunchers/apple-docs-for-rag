

- WebKit
- WKWebExtensionContext
-  hasAccessToPrivateData 

Instance Property

# hasAccessToPrivateData

A Boolean value indicating if the extension has access to private data.

iOS 18.4+iPadOS 18.4+Mac Catalyst 18.4+macOS 15.4+visionOS 2.4+

``` source
@MainActor
var hasAccessToPrivateData: Bool { get set }
```

## Discussion

If this property is true, the extension is granted permission to interact with private windows, tabs, and cookies. Access to private data should be explicitly allowed by the user before setting this property. This value should be saved and restored as needed by the app.

Note

To ensure proper isolation between private and non-private data, web views associated with private data must use a different WKUserContentController. Likewise, to be identified as a private web view and to ensure that cookies and other website data is not shared, private web views must be configured to use a non-persistent WKWebsiteDataStore.

