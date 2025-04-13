

- ReplayKit
- RPPreviewViewControllerDelegate
-  previewControllerDidFinish(\_:) 

Instance Method

# previewControllerDidFinish(\_:)

Indicates that the preview view controller is ready to be dismissed.

iOS 9.0+iPadOS 9.0+Mac Catalyst 13.0+macOS 11.0+tvOS 10.0+visionOS 1.0+

``` source
optional func previewControllerDidFinish(_ previewController: RPPreviewViewController)
```

## Parameters 

`previewController`  

The preview view controller to be dismissed.

## Discussion

When the user is finished making changes to a screen recording, your app is responsible for dismissing the view controller representing the user interface. Call dismiss(animated:completion:) after getting the message to dismiss the preview view controller.

## See Also

### Dismissing the View Controller

func previewController(RPPreviewViewController, didFinishWithActivityTypes: Set&lt;String>)

Indicates that the preview view controller is ready to be dismissed with associated activity types.

**Required**

