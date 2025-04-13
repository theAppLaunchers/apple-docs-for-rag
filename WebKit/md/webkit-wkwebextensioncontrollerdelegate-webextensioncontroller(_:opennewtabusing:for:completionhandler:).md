

- WebKit
- WKWebExtensionControllerDelegate
-  webExtensionController(\_:openNewTabUsing:for:completionHandler:) 

Instance Method

# webExtensionController(\_:openNewTabUsing:for:completionHandler:)

Called when an extension context requests a new tab to be opened.

iOS 18.4+iPadOS 18.4+Mac Catalyst 18.4+macOS 15.4+visionOS 2.4+

``` source
@MainActor
optional func webExtensionController(
    _ controller: WKWebExtensionController,
    openNewTabUsing configuration: WKWebExtension.TabConfiguration,
    for extensionContext: WKWebExtensionContext,
    completionHandler: @escaping ((any WKWebExtensionTab)?, (any Error)?) -> Void
)
```

``` source
@MainActor
optional func webExtensionController(
    _ controller: WKWebExtensionController,
    openNewTabUsing configuration: WKWebExtension.TabConfiguration,
    for extensionContext: WKWebExtensionContext
) async throws -> (any WKWebExtensionTab)?
```

## Parameters 

`controller`  

The web extension controller that is managing the extension.

`configuration`  

The configuration specifying how the new tab should be created.

`extensionContext`  

The context in which the web extension is running.

`completionHandler`  

A block to be called with the newly created tab or `nil` if the tab wasn’t created. An error should be provided if any errors occurred.

## Discussion

This method should be implemented by the app to handle requests to open new tabs. The app can decide how to handle the process based on the provided configuration and existing tabs. Once handled, the app should call the completion handler with the opened tab or `nil` if the request was declined or failed. If not implemented, the extension will be unable to open new tabs.

