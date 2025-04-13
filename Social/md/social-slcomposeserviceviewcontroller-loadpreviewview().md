

- Social
- SLComposeServiceViewController
-  loadPreviewView() 

Instance Method

# loadPreviewView()

Loads a view that displays a preview of the attachments in the extension context.

iOS 8.0+iPadOS 8.0+Mac Catalyst 13.1+

``` source
@MainActor
func loadPreviewView() -> UIView!
```

## Return Value

A view that can appropriately display a preview of the attachments in the context, or `nil` if a preview is unnecessary for the context.

## Discussion

A preview view appears next to the text editing area in a compose view. A subclass can override this method to provide a custom preview view.

