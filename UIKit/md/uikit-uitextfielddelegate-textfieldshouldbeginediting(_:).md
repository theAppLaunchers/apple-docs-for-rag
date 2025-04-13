

- UIKit
- UITextFieldDelegate
-  textFieldShouldBeginEditing(\_:) 

Instance Method

# textFieldShouldBeginEditing(\_:)

Asks the delegate whether to begin editing in the specified text field.

iOS 2.0+iPadOS 2.0+Mac Catalyst 13.1+tvOSvisionOS 1.0+

``` source
@MainActor
optional func textFieldShouldBeginEditing(_ textField: UITextField) -> Bool
```

## Parameters 

`textField`  

The text field in which editing is about to begin.

## Return Value

true if editing should begin or false if it should not.

## Discussion

The text field calls this method when the user performs an action that would normally initiate the editing of the text field’s text. Implement this method if you want to prevent editing from happening in some situations. For example, you could use this method to prevent the user from editing the text field’s contents more than once. Most of the time, you should return true to allow editing to proceed.

If you do not implement this method, the text field acts as if this method had returned true.

## See Also

### Managing editing

func textFieldDidBeginEditing(UITextField)

Tells the delegate when editing begins in the specified text field.

func textFieldShouldEndEditing(UITextField) -> Bool

Asks the delegate whether to stop editing in the specified text field.

func textFieldDidEndEditing(UITextField, reason: UITextField.DidEndEditingReason)

Tells the delegate when editing stops for the specified text field, and the reason it stopped.

func textFieldDidEndEditing(UITextField)

Tells the delegate when editing stops for the specified text field.

enum DidEndEditingReason

Constants that indicate the reason for ending editing in a text field.

