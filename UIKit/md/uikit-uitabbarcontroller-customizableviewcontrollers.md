

- UIKit
- UITabBarController
-  customizableViewControllers 

Instance Property

# customizableViewControllers

The subset of view controllers managed by this tab bar controller that can be customized.

iOS 2.0+iPadOS 2.0+Mac Catalyst 13.1+

``` source
@MainActor
var customizableViewControllers: [UIViewController]? { get set }
```

## Discussion

This property controls which items in the tab bar can be rearranged by the user. When the user taps the More item on the tab bar view, a custom interface appears displaying any items that did not fit on the main tab bar. This interface also contains an Edit button that allows the user to rearrange the items. Only the items whose associated view controllers are in this array can be rearranged from this interface. If the array is empty or the value of this property is `nil`, the tab bar does not allow any items to be rearranged.

Changing the value of the viewControllers property (either directly or using the setViewControllers(_:animated:) method) also changes the value of this property. When first assigned to the tab bar controller, all view controllers are customizable by default.

Note

Customizable tab bar controllers and the More interface are not available in tvOS.

## See Also

### Managing the view controllers

var viewControllers: [UIViewController]?

An array of the root view controllers displayed by the tab bar interface.

func setViewControllers([UIViewController]?, animated: Bool)

Sets the root view controllers of the tab bar controller.

var moreNavigationController: UINavigationController

The view controller that manages the More navigation interface.

