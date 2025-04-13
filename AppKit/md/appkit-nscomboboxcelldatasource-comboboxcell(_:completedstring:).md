

- AppKit
- NSComboBoxCellDataSource
-  comboBoxCell(\_:completedString:) 

Instance Method

# comboBoxCell(\_:completedString:)

Returns the item from the combo box’s pop-up list that matches the text entered by the user.

macOS

``` source
optional func comboBoxCell(
    _ comboBoxCell: NSComboBoxCell,
    completedString uncompletedString: String
) -> String?
```

## Parameters 

`comboBoxCell`  

The combo box cell.

`uncompletedString`  

The substring containing the text the user typed into the text field of the combo box cell.

## Return Value

The completed string, from the items in the pop-up list, that matches the text entered by the user. Your implementation should return the first complete string that starts with `uncompletedString`.

## Discussion

An `NSComboBoxCell` object uses this method to perform incremental—or “smart”—searches when the user types into the text field.

As the user types in the text field, the receiver uses this method to search for items from the pop-up list that start with what the user has typed. The receiver adds the new text to the end of the field and selects the new text, so when the user types another character, it replaces the new text.

If you don’t implement this method, the receiver does not perform incremental searches.

## See Also

### Instance Methods

func comboBoxCell(NSComboBoxCell, indexOfItemWithStringValue: String) -> Int

Invoked by an `NSComboBoxCell` object to synchronize the pop-up list’s selected item with the text field’s contents.

func comboBoxCell(NSComboBoxCell, objectValueForItemAt: Int) -> Any

Returns the object that corresponds to the item at the given index in the combo box cell.

func numberOfItems(in: NSComboBoxCell) -> Int

Returns the number of items managed for the combo box cell by your data source object.

