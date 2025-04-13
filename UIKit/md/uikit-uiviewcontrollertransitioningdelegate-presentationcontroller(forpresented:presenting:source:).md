

- UIKit
- UIViewControllerTransitioningDelegate
-  presentationController(forPresented:presenting:source:) 

Instance Method

# presentationController(forPresented:presenting:source:)

Asks your delegate for the custom presentation controller to use for managing the view hierarchy when presenting a view controller.

iOS 8.0+iPadOS 8.0+Mac Catalyst 13.1+tvOSvisionOS 1.0+

``` source
@MainActor
optional func presentationController(
    forPresented presented: UIViewController,
    presenting: UIViewController?,
    source: UIViewController
) -> UIPresentationController?
```

## Parameters 

`presented`  

The view controller being presented.

`presenting`  

The view controller that is presenting the view controller in the `presented` parameter. The object in this parameter could be the root view controller of the window, a parent view controller that is marked as defining the current context, or the last view controller that was presented. This view controller may or may not be the same as the one in the `source` parameter. This parameter may also be `nil` to indicate that the presenting view controller will be determined later.

`source`  

The view controller whose present(_:animated:completion:) method was called to initiate the presentation process.

## Return Value

The custom presentation controller for managing the modal presentation.

## Discussion

When you present a view controller using the UIModalPresentationStyle.custom presentation style, the system calls this method and asks for the presentation controller that manages your custom style. If you implement this method, use it to create and return the custom presentation controller object that you want to use to manage the presentation process.

If you don’t implement this method, or if your implementation of this method returns `nil`, the system uses a default presentation controller object. The default presentation controller doesn’t add any views or content to the view hierarchy.

