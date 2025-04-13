

- WebKit
- WKWebExtensionContext
-  hasActiveUserGesture(in:) 

Instance Method

# hasActiveUserGesture(in:)

Indicates if a user gesture is currently active in the specified tab.

iOS 18.4+iPadOS 18.4+Mac Catalyst 18.4+macOS 15.4+visionOS 2.4+

``` source
@MainActor
func hasActiveUserGesture(in tab: any WKWebExtensionTab) -> Bool
```

## Parameters 

`tab`  

The tab for which to check for an active user gesture.

## Discussion

An active user gesture may influence the availability of certain permissions, such as `activeTab`. User gestures can be triggered by various user interactions with the web extension, including clicking on extension menu items, executing extension commands, or interacting with extension actions. A tab as having an active user gesture enables the extension to access features that require user interaction.

## See Also

### Related Documentation

func userGesturePerformed(in: any WKWebExtensionTab)

Should be called by the app when a user gesture is performed in a specific tab.

