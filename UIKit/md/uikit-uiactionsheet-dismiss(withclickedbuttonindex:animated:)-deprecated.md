

- UIKit
- UIActionSheet
-  dismiss(withClickedButtonIndex:animated:) Deprecated

Instance Method

# dismiss(withClickedButtonIndex:animated:)

Dismisses the action sheet immediately using an optional animation.

iOS 2.0–8.3DeprecatediPadOS 2.0–8.3DeprecatedMac Catalyst 13.1–13.1Deprecated

``` source
@MainActor
func dismiss(
    withClickedButtonIndex buttonIndex: Int,
    animated: Bool
)
```

## Parameters 

`buttonIndex`  

The index of the button that was clicked. Button indices start at `0`.

`animated`  

Specify true to animate the dismissal of the action sheet or false to remove the action sheet without an animation.

## Discussion

You can use this method to dismiss the action sheet programmatically as needed. The action sheet also calls this method itself in response to the user tapping one of the buttons in the action sheet.

In iOS 4.0, you may want to call this method whenever your application moves to the background. An action sheet is not dismissed automatically when an application moves to the background. This behavior differs from previous versions of the operating system, where they were canceled automatically when the application was terminated. Dismissing the action sheet gives your application a chance to save changes or abort the operation and perform any necessary cleanup in case your application is terminated later.

