

- UIKit
- UIDocumentInteractionControllerDelegate
-  documentInteractionControllerViewControllerForPreview(\_:) 

Instance Method

# documentInteractionControllerViewControllerForPreview(\_:)

Called when a document interaction controller needs a view controller for presenting a document preview.

iOS 3.2+iPadOS 3.2+Mac Catalyst 13.1+visionOS 1.0+

``` source
@MainActor
optional func documentInteractionControllerViewControllerForPreview(_ controller: UIDocumentInteractionController) -> UIViewController
```

## Parameters 

`controller`  

The document interaction controller requesting the parent view controller.

## Return Value

The view controller to use when presenting the document preview. The return value must not be `nil`.

## Discussion

Although technically optional, this method is required if your application attempts to display a preview for a document. The view controller returned by this method is used as the parent for the document preview.

If you return a navigation controller from this method, the document interaction controller is pushed onto the navigation stack using the standard navigation controller animations. If you return any other type of view controller, the document interaction controller is displayed modally, in which case, the view controller you return must be capable of presenting a modal view controller.

## See Also

### Configuring the parent view controller

func documentInteractionControllerViewForPreview(UIDocumentInteractionController) -> UIView?

Called when a document interaction controller needs the starting point for animating the display of a document preview.

func documentInteractionControllerRectForPreview(UIDocumentInteractionController) -> CGRect

Called when a document interaction controller needs the rectangle to use as the starting point for animating the display of a document preview.

