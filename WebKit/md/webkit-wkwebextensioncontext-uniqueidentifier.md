

- WebKit
- WKWebExtensionContext
-  uniqueIdentifier 

Instance Property

# uniqueIdentifier

A unique identifier used to distinguish the extension from other extensions and target it for messages.

iOS 18.4+iPadOS 18.4+Mac Catalyst 18.4+macOS 15.4+visionOS 2.4+

``` source
@MainActor
var uniqueIdentifier: String { get set }
```

## Discussion

The default value is a unique value that matches the host in the default base URL. The identifier can be any value that is unique. Setting is only allowed when the context is not loaded. This value is accessible by the extension via `browser.runtime.id` and is used for messaging the extension via `browser.runtime.sendMessage()`.

