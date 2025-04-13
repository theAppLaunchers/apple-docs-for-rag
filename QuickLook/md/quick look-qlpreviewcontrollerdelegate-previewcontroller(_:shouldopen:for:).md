

- Quick Look
- QLPreviewControllerDelegate
-  previewController(\_:shouldOpen:for:) 

Instance Method

# previewController(\_:shouldOpen:for:)

Tells the delegate that the preview controller is trying to open a URL.

iOS 8.0+iPadOS 8.0+Mac Catalyst 13.1+visionOS 1.0+

``` source
optional func previewController(
    _ controller: QLPreviewController,
    shouldOpen url: URL,
    for item: any QLPreviewItem
) -> Bool
```

## Parameters 

`controller`  

The Quick Look preview controller that’s asking the delegate to handle a user tapping a URL.

`url`  

The URL, from the displayed preview, that the user taps.

`item`  

The item displaying in the preview.

## Return Value

A Boolean value indicating whether to open the URL in the `url` parameter.

## Discussion

The system invokes this method when the user taps a URL link in a preview. If you return true, the Quick Look preview controller invokes the openURL(_:) method on the UIApplication object, sending it the value of the `url` parameter. If you return false, the system doesn’t invoke the openURL(_:) method.

If you don’t implement this method, it defaults to returning true.

Note

The system doesn’t call this delegate method for Mac apps built with Mac Catalyst.

