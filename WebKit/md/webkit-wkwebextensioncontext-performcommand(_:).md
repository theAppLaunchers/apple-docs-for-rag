

- WebKit
- WKWebExtensionContext
-  performCommand(\_:) 

Instance Method

# performCommand(\_:)

Performs the specified command, triggering events specific to this extension.

iOS 18.4+iPadOS 18.4+Mac Catalyst 18.4+macOS 15.4+visionOS 2.4+

``` source
@MainActor
func performCommand(_ command: WKWebExtension.Command)
```

## Parameters 

`command`  

The command to be performed.

## Discussion

This method performs the given command as if it was triggered by a user gesture within the context of the focused window and active tab.

