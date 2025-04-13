

- UIKit
- View controllers
-  Creating a custom container view controller 

Article

# Creating a custom container view controller

Create a composite interface by combining content from one or more view controllers with other custom views.

## Overview

Container view controllers promote better encapsulation by separating out your content from how you display that content onscreen. Unlike a content view controller that displays your app’s data, a container view controller displays other view controllers, arranging them onscreen and handling navigation between them.

A container view controller is still a view controller, so you display it in a window or present it like any other view controller. A container view controller also manages a composite interface, incorporating the views from one or more child view controllers into its own view hierarchy. Each child continues to manage its own view hierarchy, but the container manages the position and size of that child’s root view.

Many container view controllers facilitate navigation between different parts of your app’s content. Examples include UINavigationController, UITabBarController, and UIPageViewController, which help users navigate between different view controllers. You can also use container view controllers to organize the content you have more efficiently. For example, UISplitViewController displays two view controllers side-by-side on iPad. The only difference between navigation and organization is that navigation requires custom API to change the child view controllers; otherwise, the implementations are identical.

### Add a child view controller programmatically to your content

If your container view controller changes its child view controllers dynamically, it’s easier to add those children programmatically. Custom navigation interfaces facilitate navigation by changing their child view controllers, and you might also change child view controllers as part of configuring your interface.

For each new child view controller you add to your interface, perform the following steps in order:

1.  Call the addChild(_:) method of your container view controller to configure the containment relationship.

2.  Add the child’s root view to your container’s view hierarchy.

3.  Add constraints to set the size and position of the child’s root view.

4.  Call the didMove(toParent:) method of the child view controller to notify it that the transition is complete.

The following example code instantiates a new child view controller from a storyboard and embeds it as a child of the current view controller. After calling addChild(_:), the code adds the child’s view to the view hierarchy and sets up some layout constraints to size and position it. At the end of the process, it notifies the child.

```
// Create a child view controller and add it to the current view controller.
let storyboard = UIStoryboard(name: "Main", bundle: .main)
if let viewController = storyboard.instantiateViewController(identifier: "imageViewController")
                                    as? ImageViewController {
   // Add the view controller to the container.
   addChild(viewController)
   view.addSubview(viewController.view)

   // Create and activate the constraints for the child’s view.
   onscreenConstraints = configureConstraintsForContainedView(containedView: viewController.view,
                             stage: .onscreen)
   NSLayoutConstraint.activate(onscreenConstraints)

   // Notify the child view controller that the move is complete.       
   viewController.didMove(toParent: self)
}

```

Establishing a container-child relationship between view controllers prevents UIKit from interfering with your interface unintentionally. UIKit normally routes information to each of your app’s view controllers independently. When a container-child relationship exists, UIKit routes many requests through the container view controller first, giving it a chance to alter the behavior for any child view controllers. For example, a container view controller may override the traits of its children, forcing them to adopt a specific appearance or behavior.

### Remove a child view controller from your content

To remove a child view controller from your container, perform the following steps in order:

1.  Call the child’s willMove(toParent:) method with the value `nil`.

2.  Deactivate or remove any constraints for the child’s root view.

3.  Call removeFromSuperview() on the child’s root view to remove it from the view hierarchy.

4.  Call the child’s removeFromParent() method to finalize the end of the container-child relationship.

Breaking a container-child relationship tells UIKit that your container view controller is no longer displaying the child’s content. You can still maintain other references to the child view controller. For example, UINavigationController manages a stack of child view controllers, but it maintains a container-child relationship with only one or two of those children at any given time.

### Embed a child view controller in your storyboard UI

If your container view controller organizes content, and doesn’t change that content later, configure your UI using container views. A container view is a proxy view that stands in for the content of a child view controller. When you add one to your interface, it looks like a normal view, but it has an attached view controller.

Size and position a container view the same way you would other views in your interface. Add constraints to specify the size and position of the view for different devices and in different configurations. However, don’t add any subviews to the container view itself. Instead, add them to the view of the attached view controller.

When you instantiate a view controller that contains one or more container views, UIKit also instantiates the associated child view controllers. After creating the new view controllers, UIKit adds them as children of the original view controller you requested. You don’t need to call addChild(_:) yourself.

### Support additional container behaviors

Consider implementing the following additional behaviors in your custom container view controllers:

- Override show(_:sender:), and use it to present a new child view controller.

- Override showDetailViewController(_:sender:), as needed, to present a secondary child view controller.

- Update additionalSafeAreaInsets to account for decoration views that might obscure the content of your children.

- Call setOverrideTraitCollection(_:forChild:) to change the traits of your child view controllers. For example, you might designate a child view controller as always horizontally or vertically compact.

- Override childForScreenEdgesDeferringSystemGestures or childForHomeIndicatorAutoHidden to let a child view controller determine the behavior for system gestures.

- Override allowedChildrenForUnwinding(from:) to limit the set of child view controllers that are targets of an unwind segue action.

For more information, see the descriptions in UIViewController.

## See Also

### Container view controllers

class UISplitViewController

A container view controller that implements a hierarchical interface.

class UINavigationController

A container view controller that defines a stack-based scheme for navigating hierarchical content.

class UINavigationBar

Navigational controls that display in a bar along the top of the screen, usually in conjunction with a navigation controller.

class UINavigationItem

The items that a navigation bar displays when the associated view controller is visible.

class UITabBarController

A container view controller that manages a multiselection interface, where the selection determines which child view controller to display.

class UITabBar

A control that displays one or more buttons in a tab bar for selecting between different subtasks, views, or modes in an app.

class UITabBarItem

An object that describes an item in a tab bar.

class UITab

An object that manages a tab in a tab bar.

class UISearchTab

A tab subclass that represents the system’s search tab.

class UITabGroup

An object that manages a collection of tab objects.

class UIPageViewController

A container view controller that manages navigation between pages of content, where a subview controller manages each page.

