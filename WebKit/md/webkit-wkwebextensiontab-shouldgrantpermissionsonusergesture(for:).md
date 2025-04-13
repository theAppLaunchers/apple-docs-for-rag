

- WebKit
- WKWebExtensionTab
-  shouldGrantPermissionsOnUserGesture(for:) 

Instance Method

# shouldGrantPermissionsOnUserGesture(for:)

Called to determine if permissions should be granted for the tab on user gesture.

iOS 18.4+iPadOS 18.4+Mac Catalyst 18.4+macOS 15.4+visionOS 2.4+

``` source
@MainActor
optional func shouldGrantPermissionsOnUserGesture(for context: WKWebExtensionContext) -> Bool
```

## Parameters 

`context`  

The context in which the web extension is running.

## Discussion

This method allows the app to control granting of permissions on a per-tab basis when triggered by a user gesture. Implementing this method enables the app to dynamically manage `activeTab` permissions based on the tab’s current state, the content being accessed, or other custom criteria.

