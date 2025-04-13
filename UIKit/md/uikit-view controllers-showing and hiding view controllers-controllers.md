

- UIKit
- View controllers
-  Showing and hiding view controllers 

# Showing and hiding view controllers

Display view controllers using different techniques, and pass data between them during transitions.

## Overview

You change your app’s interface by presenting and dismissing view controllers. Every window has a root view controller, which provides the initial content for your window. Presenting a new view controller changes that content by installing a new set of views in the window. When you no longer need the view controller, dismissing it removes its views from the window. You present view controllers in one of these ways:

- Configure presentations visually in your storyboard.

- Embed them in a container view controller.

- Call methods of UIViewController directly.

Each technique gives you different amounts of control over the presentation and dismissal process.

### Specify presentations visually in your storyboard file

Using segues in your storyboard is the recommended way to present and dismiss view controllers. A segue is a visual representation of a transition from one view controller to another. A segue starts with an action such as a button tap or table-row selection in the initial view controller. When that action occurs, UIKit creates the view controller at the other end of the segue and presents it automatically. Because you create and configure segues in your storyboard, you can change them very quickly.

Start a segue from any object that implements an action method, such as a control or gesture recognizer. You may also start segues from table rows and collection view cells.

1.  Right-click the control or object in your current view controller.

2.  Drag the cursor to the view controller you want to present.

3.  Select the kind of segue you want from the list that Xcode provides.

The storyboard shows segues as an arrow between two view controllers. Selecting the segue displays information about it, including the kind of presentation you want UIKit to perform. You can modify the presentation type or configure additional details, such as a segue identifier. You use this information at runtime to customize the segue further, as described in Customizing the behavior of segue-based presentations.

For information about how to dismiss a view controller in your storyboards, see Dismissing a view controller with an unwind segue.

### Let the current context define the presentation technique

Reusing the same view controller in multiple places creates a potential problem: presenting it in different ways based on the current context. For example, you might want to embed it in a navigation controller in one instance, but present it modally in another. UIKit solves this problem with the show(_:sender:) and showDetailViewController(_:sender:) methods of UIViewController, which present the view controller in the most appropriate way for the current context.

When you call the show(_:sender:) or showDetailViewController(_:sender:) method, UIKit determines the most appropriate context for the presentation. Specifically, it calls the targetViewController(forAction:sender:) method to search for a parent view controller that implements the corresponding `show` method. If a parent implements the method and wants to handle the presentation, UIKit calls the parent’s implementation. A UINavigationController object’s implementation of the show(_:sender:) method pushes the new view controller onto its navigation stack. If no view controller handles the presentation, UIKit presents the view controller modally.

The following code example creates a view controller and shows it using the show(_:sender:) method. The code is equivalent to creating a segue with the kind set to Show.

```
@IBAction func showSecondViewController() {
    let storyboard = UIStoryboard(name: "Main", bundle: nil)
    let secondVC = storyboard.instantiateViewController(identifier: "SecondViewController")

    show(secondVC, sender: self)
}
```

After showing a view controller, use the current context to determine how to dismiss it. Calling the dismiss(animated:completion:) method might not always be the most appropriate option. For example, don’t call that method if a navigation controller added the view controller to its navigation stack. Instead, use the presentingViewController, splitViewController, navigationController, and tabBarController properties to determine the current context, and to take appropriate actions in response. That response might also include modifying your view controller’s UI to hide a Done button or other controls for dismissing the UI.

Note

When implementing a custom container view controller, implement the show(_:sender:) and showDetailViewController(_:sender:) methods to handle presentations. For more information, see Creating a custom container view controller.

### Embed a view controller inside a container view controller

A container view controller embeds content from one or more child view controllers, and presents the combined interface onscreen. Embedding a child view controller presents it using a container-specific approach. For example, a navigation controller initially positions the child view controller offscreen and then animates it into position onscreen.

The standard UIKit container view controllers work with segues and the show(_:sender:) and showDetailViewController(_:sender:) methods to embed view controllers as children. They also define additional API for adding and removing child view controllers programmatically. Use segues and the show methods to handle most transitions. Use the methods in the following table to perform one-time configuration of your view controller, for example when restoring your app’s UI to a previous state.

| Container | Presentation options |
|----|----|
| UISplitViewController | Replace the two initial view controllers using the viewControllers property. The first (primary) view controller appears in the leading pane and the second (detail) view controller appears in the trailing pane. |
| UINavigationController | Replace the contents of the navigation stack using the viewControllers property. Add or remove a subset of view controllers simultaneously using the setViewControllers(_:animated:) method. |
| UITabBarController | Replace the initial tabs using the viewControllers property. Change the current tabs dynamically using the setViewControllers(_:animated:) method. |
| UIPageViewController | Provide all child view controllers using a UIPageViewControllerDataSource object. |

Always use the container view controller’s API to remove or replace a presented view controller.

### Present a view controller modally

Use modal presentations to create temporary interruptions in your app’s workflow, such as prompting the user for important information. A modal presentation covers the current view controller wholly or partially, depending on the presentation style you use. Full-screen presentations always replace the previous content, but sheet-style presentations may leave some of the underlying content visible. The actual appearance of each presentation style depends on the current trait environment.

To configure a modal presentation, create the new view controller and call the present(_:animated:completion:) method. That method animates the new view controller into position using the UIModalPresentationStyle.automatic style and the UIModalTransitionStyle.coverVertical transition animation. To change the styles, modify the modalPresentationStyle and modalTransitionStyle properties of the view controller you present. The following code example changes both of these styles to create a full-screen presentation using a cross-dissolve animation.

```
    @IBAction func presentSecondViewController() {
        let storyboard = UIStoryboard(name: "Main", bundle: nil)
        let secondVC = storyboard.instantiateViewController(identifier: "SecondViewController")

        secondVC.modalPresentationStyle = .fullScreen
        secondVC.modalTransitionStyle = .crossDissolve

        present(secondVC, animated: true, completion: nil)
    }
```

To dismiss a modally presented view controller, call the view controller’s dismiss(animated:completion:) method.

## Topics

### Segue management

Customizing the behavior of segue-based presentations

Pass data between view controllers during a segue, and programmatically control when segues occur.

Dismissing a view controller with an unwind segue

Configure an unwind segue in your storyboard file that dynamically chooses the most appropriate view controller to display next.

## See Also

### Content view controllers

Displaying and managing views with a view controller

Build a view controller in storyboards, configure it with custom views, and fill those views with your app’s data.

class UIViewController

An object that manages a view hierarchy for your UIKit app.

class UITableViewController

A view controller that specializes in managing a table view.

class UICollectionViewController

A view controller that specializes in managing a collection view.

protocol UIContentContainer

A set of methods for adapting the contents of your view controllers to size and trait changes.

