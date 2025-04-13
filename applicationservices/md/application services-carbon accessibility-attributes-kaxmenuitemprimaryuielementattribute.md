

- Application Services
- Carbon Accessibility
- Attributes
-  kAXMenuItemPrimaryUIElementAttribute 

Global Variable

# kAXMenuItemPrimaryUIElementAttribute

macOS 10.4+

``` source
var kAXMenuItemPrimaryUIElementAttribute: String { get }
```

## Discussion

The accessibility object representing the primary menu item in a group of dynamic menu items. Dynamic menu item are commands that change when the user presses a modifier key, such as Minimize Window and Minimize All Windows. Within each group, each dynamic menu item’s accessibility object includes this attribute and in each case the attribute’s value is the accessibility object representing the primary menu item.

