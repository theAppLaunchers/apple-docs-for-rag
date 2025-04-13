

- AppKit
- NSMenuItemValidation
-  validateMenuItem(\_:) 

Instance Method

# validateMenuItem(\_:)

Implemented to override the default action of enabling or disabling a specific menu item.

macOS

``` source
@MainActor
func validateMenuItem(_ menuItem: NSMenuItem) -> Bool
```

**Required**

## Parameters 

`menuItem`  

An NSMenuItem object that represents the menu item.

## Return Value

true to enable `menuItem`, false to disable it.

## Discussion

The object implementing this method must be the target of `menuItem`. You can determine which menu item `menuItem` is by querying it for its tag or action.

The following example disables the menu item associated with the `nextRecord` action method when the selected line in a table view is the last one; conversely, it disables the menu item with `priorRecord` as its action method when the selected row is the first one in the table view. (The `countryOrRegionKeys` array contains names that appear in the table view.)

```
- (BOOL)validateMenuItem:(NSMenuItem *)item {
    int row = [tableView selectedRow];
    if ([item action] == @selector(nextRecord) &&
        (row == [countryOrRegionKeys indexOfObject:[countryOrRegionKeys lastObject]])) {
        return NO;
    }
    if ([item action] == @selector(priorRecord) && row == 0) {
        return NO;
    }
    return YES;
}
```

