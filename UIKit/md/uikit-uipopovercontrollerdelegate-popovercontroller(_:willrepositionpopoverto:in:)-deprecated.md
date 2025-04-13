

- UIKit
- UIPopoverControllerDelegate
-  popoverController(\_:willRepositionPopoverTo:in:) Deprecated

Instance Method

# popoverController(\_:willRepositionPopoverTo:in:)

Tells the delegate that the popover controller needs to change the popover’s location in its view.

iOS 7.0–9.0DeprecatediPadOS 7.0–9.0DeprecatedMac Catalyst 13.1–13.1DeprecatedtvOSDeprecated

``` source
@MainActor
optional func popoverController(
    _ popoverController: UIPopoverController,
    willRepositionPopoverTo rect: UnsafeMutablePointer,
    in view: AutoreleasingUnsafeMutablePointer
)
```

## Parameters 

`popoverController`  

The popover controller changing the position of its content.

`rect`  

On input, the proposed rectangle for the popover. This popover is in the coordinate space of the view in the `view` parameter. If you want to propose a different rectangle for the popover, put the new value in this parameter.

`view`  

On input, the proposed view for containing the popover. If you want to propose a different view for the popover, put the new view in this parameter.

## Discussion

For popovers that were presented using the present(from:in:permittedArrowDirections:animated:) method, the popover controller calls this method when the interface orientation changes. Your delegate can use this method to adjust the proposed position of the popover. The popover controller does not call this method if you presented the popover from a bar button item.

