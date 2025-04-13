

- UIKit
- UISearchController
- UISearchController.ScopeBarActivation
-  UISearchController.ScopeBarActivation.manual 

Case

# UISearchController.ScopeBarActivation.manual

A mode that gives you manual control over when to show and hide the scope bar.

iOS 16.0+iPadOS 16.0+Mac Catalyst 16.0+visionOS 1.0+

``` source
case manual
```

## Discussion

When you use this mode, you control when to show and hide the scope bar through the showsScopeBar property on the searchBar of the UISearchController.

## See Also

### Constants

case automatic

A mode in which the system automatically determines when to show and hide the scope bar.

case onTextEntry

A mode in which the search controller shows the scope bar when typing begins in the search field, and hides it after search cancellation.

case onSearchActivation

A mode in which the search controller shows the scope bar when search becomes active, and hides it after search cancellation.

