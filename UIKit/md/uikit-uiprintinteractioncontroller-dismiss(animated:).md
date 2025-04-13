

- UIKit
- UIPrintInteractionController
-  dismiss(animated:) 

Instance Method

# dismiss(animated:)

Dismisses the printing-options sheet or popover.

iOS 4.2+iPadOS 4.2+Mac Catalyst 13.1+visionOS 1.0+

``` source
@MainActor
func dismiss(animated: Bool)
```

## Parameters 

`animated`  

true to animate the dismissal, otherwise false.

## Discussion

You should dismiss the printing options when they are presented in a sheet or animated from a rectangle *and* the user changes the orientation of the device. (This, of course, assumes your application responds to orientation changes.) You should then present the printing options again once the new orientation takes effect. You can observe the willChangeStatusBarOrientationNotification notification to find out when the device orientation is about to change.

## See Also

### Presenting the printing user interface

func present(animated: Bool, completionHandler: UIPrintInteractionController.CompletionHandler?) -> Bool

Presents the iPhone printing user interface in a sheet, optionally animating it to slide up from the bottom of the screen.

func present(from: UIBarButtonItem, animated: Bool, completionHandler: UIPrintInteractionController.CompletionHandler?) -> Bool

Presents the iPad printing user interface in a popover view, optionally animating it from a bar-button item.

func present(from: CGRect, in: UIView, animated: Bool, completionHandler: UIPrintInteractionController.CompletionHandler?) -> Bool

Presents the iPad printing user interface in a popover view, optionally animating it from any area in a view.

