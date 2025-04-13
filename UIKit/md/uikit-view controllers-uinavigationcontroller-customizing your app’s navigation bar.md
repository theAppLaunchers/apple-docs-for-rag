

- UIKit
- View controllers
- UINavigationController
-  Customizing your app’s navigation bar 

Sample Code

# Customizing your app’s navigation bar

Create custom titles, prompts, and buttons in your app’s navigation bar.

Download

iOS 14.1+iPadOS 14.1+Xcode 13.3+

## Overview

Use UINavigationBar to display your app’s navigational controls in a bar along the top of the iOS device’s screen. You can also design a distinctive navigation bar that matches your app’s design and creates intuitive interaction for your users.

This sample code project demonstrates how to use `UINavigationController` and `UIViewController` classes as building blocks in your application’s user interface.

The project walks you through a set of examples that customize the look and behavior of UINavigationController and UINavigationBar, including views, prompts, buttons and titles of your application’s navigation bar.

The sample demonstrates different ways to modify the navigation bar directly using the appearance proxy, and indirectly by modifying the view controller’s UINavigationItem. The levels of customization include varying bar styles and applying custom left and right buttons known as UIBarButtonItem.

### Change the bar style

The sample demonstrates changing the bar style to match the overall appearance of an app’s design.

A user changes the navigation bar’s style, or UIBarStyle, by tapping the “Style” button to the left of the main page. This button opens an action sheet where users can change the background’s appearance to default, black-opaque, or black- translucent.

To change the bar style to black-translucent:

```
self.navigationController!.navigationBar.barStyle = .black
self.navigationController!.navigationBar.isTranslucent = false
self.navigationController!.navigationBar.titleTextAttributes = [.foregroundColor: UIColor.white]
```

Note

A navigation controller determines its preferredStatusBarStyle based on the navigation bar style. As a result, the status bar matches the bar style, without any extra code required.

### Customize the right view

The right side of the navigation bar options for customization include applying a custom `UIView` or using a `UIBarButtonItem`.

The sample demonstrates placing three kinds of `UIBarButtonItems` on the right side of the navigation bar: a button with a title, a button with an image, and a button with a `UISegmentedControl`. An additional segmented control allows the user to toggle between the three buttons. The initial bar button is defined in the storyboard, by dragging a `UIBarButtonItem` out of the object library and into the navigation bar. The sample also shows how to create and add each button type using code.

This sample shows how to set a segmented control as the right bar button item:

```
let segmentBarItem = UIBarButtonItem(customView: segmentedControl)
navigationItem.rightBarButtonItem = segmentBarItem
```

### Customize the title view

Another option is configuring the navigation bar to use a `UIView` as the title, using `UISegmentedControl` as the center custom title view.

This sample shows how to set a segmented control as the title view:

```
self.navigationItem.titleView = segmentedControl
```

### Modify the navigation prompt

The navigation bar can also include a prompt or single line of text at the top.

The sample demonstrates how to use the prompt property of a `UINavigationItem` to display a custom line of text above the navigation bar.

Here’s how to set the navigation item’s prompt:

```
navigationItem.prompt = NSLocalizedString("Navigation prompts appear at the top.", comment: "")
```

### Customize the navigation bar appearance

Apply a custom background to a `UINavigationBar` by adding a bar tint color or background image.

The sample sets the background image of a navigation bar like this:

```
let navBar = self.navigationController!.navigationBar

let standardAppearance = UINavigationBarAppearance()
standardAppearance.configureWithOpaqueBackground()
standardAppearance.backgroundImage = backImageForDefaultBarMetrics

let compactAppearance = standardAppearance.copy()
compactAppearance.backgroundImage = backImageForLandscapePhoneBarMetrics

navBar.standardAppearance = standardAppearance
navBar.scrollEdgeAppearance = standardAppearance
navBar.compactAppearance = compactAppearance
if #available(iOS 15.0, *) { // For compatibility with earlier iOS.
    navBar.compactScrollEdgeAppearance = compactAppearance
}
```

### Customize back button titles

Users can quickly switch between different stack levels with a tap and hold on the back button. The sample shows this by pushing ten view controllers on the current navigation stack to demonstrate that back button titles can be customized for each view controller level in the stack.

### Customize the back button with an image

It’s also possible to use an image as the back button without any back button text and without the back arrow that normally appears next to the back button. The sample sets the back button UINavigationBar appearance like this:

```
// For Back button customization, setup the custom image for UINavigationBar inside CustomBackButtonNavController.
let backButtonBackgroundImage = UIImage(systemName: "list.bullet")
let barAppearance =
    UINavigationBar.appearance(whenContainedInInstancesOf: [CustomBackButtonNavController.self])
barAppearance.backIndicatorImage = backButtonBackgroundImage
barAppearance.backIndicatorTransitionMaskImage = backButtonBackgroundImage

// Nudge the back UIBarButtonItem image down a bit.
let barButtonAppearance =
    UIBarButtonItem.appearance(whenContainedInInstancesOf: [CustomBackButtonNavController.self])
barButtonAppearance.setBackButtonTitlePositionAdjustment(UIOffset(horizontal: 0, vertical: -5), for: .default)
```

Then, it removes the back button text:

```
let backBarButton = UIBarButtonItem(title: "", style: .plain, target: nil, action: nil)
navigationItem.backBarButtonItem = backBarButton
```

### Modify the large title in the navigation bar

Another option for customizing the navigation bar includes setting its title at a larger size, thus increasing the size of the `UINavigationBar`. For more information, refer to the `LargeTitleViewController` source file in this sample.

The code below shows how the sample sets the background image of a navigation bar:

```
self.navigationController?.navigationBar.prefersLargeTitles = true
```

### Change navigation bar appearance

Use UINavigationBarAppearance and UIBarButtonItemAppearance to change the appearance of the navigation bar.

```
// Make the navigation bar's title with red text.
let appearance = UINavigationBarAppearance()
appearance.configureWithOpaqueBackground()
appearance.backgroundColor = UIColor.systemRed
appearance.titleTextAttributes = [.foregroundColor: UIColor.lightText] // With a red background, make the title more readable.
navigationItem.standardAppearance = appearance
navigationItem.scrollEdgeAppearance = appearance
navigationItem.compactAppearance = appearance // For iPhone small navigation bar in landscape.

// Make all buttons with green text.
let buttonAppearance = UIBarButtonItemAppearance()
buttonAppearance.normal.titleTextAttributes = [.foregroundColor: UIColor.systemGreen]
navigationItem.standardAppearance?.buttonAppearance = buttonAppearance
navigationItem.compactAppearance?.buttonAppearance = buttonAppearance // For iPhone small navigation bar in landscape.

// Make the done style button with yellow text.
let doneButtonAppearance = UIBarButtonItemAppearance()
doneButtonAppearance.normal.titleTextAttributes = [.foregroundColor: UIColor.systemYellow]
navigationItem.standardAppearance?.doneButtonAppearance = doneButtonAppearance
navigationItem.compactAppearance?.doneButtonAppearance = doneButtonAppearance // For iPhone small navigation bar in landscape.
```

### Attach a menu to a bar button item

A menu attachment provides extended and easy access to application features in one place. The sample attaches a UIMenu to the right side `UIBarButtonItem` control:

```
let barButtonMenu = UIMenu(title: "", children: [
    UIAction(title: NSLocalizedString("Copy", comment: ""), image: UIImage(systemName: "doc.on.doc"), handler: menuHandler),
    UIAction(title: NSLocalizedString("Rename", comment: ""), image: UIImage(systemName: "pencil"), handler: menuHandler),
    UIAction(title: NSLocalizedString("Duplicate", comment: ""), image: UIImage(systemName: "plus.square.on.square"), handler: menuHandler),
    UIAction(title: NSLocalizedString("Move", comment: ""), image: UIImage(systemName: "folder"), handler: menuHandler)
])
optionsBarItem.menu = barButtonMenu
```

## See Also

### Configuring navigation bars

var navigationBar: UINavigationBar

The navigation bar managed by the navigation controller.

func setNavigationBarHidden(Bool, animated: Bool)

Sets whether the navigation bar is hidden.

