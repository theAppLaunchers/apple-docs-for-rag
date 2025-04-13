

- AppKit
- NSComboBoxCell
-  completedString(\_:) 

Instance Method

# completedString(\_:)

Returns a string from the combo box’s pop-up list that starts with the given substring.

macOS

``` source
@MainActor
func completedString(_ string: String) -> String?
```

## Parameters 

`string`  

The substring to search for. This is what the user entered in the combo box’s text field.

## Return Value

The string from the combo box’s pop-up list that starts with the specified substring or `nil` if there is no such string.

## Discussion

The default implementation of this method first checks whether the combo box uses a data source and whether the data source responds to comboBox:completedString: or comboBoxCell:completedString:. If so, the combo box cell returns that method’s return value. Otherwise, this method goes through the combo box’s items one by one and returns an item that starts with `substring`.

Override this method only if your subclass completes strings differently. The overriding method does not need to call the superclass’s method. Generally, you do not need to call this method directly.

## See Also

### Completing the Text Field

var completes: Bool

A Boolean value that indicates if the combo box tries to complete text entered by the user.

