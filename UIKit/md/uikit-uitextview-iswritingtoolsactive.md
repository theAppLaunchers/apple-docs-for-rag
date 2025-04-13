

- UIKit
- UITextView
-  isWritingToolsActive 

Instance Property

# isWritingToolsActive

A Boolean value that indicates whether the writing tools are currently interacting with the text view’s content.

iOS 18.0+iPadOS 18.0+Mac Catalyst 18.0+visionOS 2.4+

``` source
@MainActor
var isWritingToolsActive: Bool { get }
```

## Discussion

Use this property to determine when someone is using the writing tools to rewrite text in the current text view. When writing tools are active, the system can change significant portions of the text view’s content. You might use this property to prevent your app from performing actions that interfere with those changes. For example, you might stop synchronizing text to iCloud while the UI is active.

To receive notifications when writing tools interactions start and stop, implement the textViewWritingToolsWillBegin(_:) and textViewWritingToolsDidEnd(_:) delegate methods.

