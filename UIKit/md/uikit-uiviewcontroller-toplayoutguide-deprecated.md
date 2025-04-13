

- UIKit
- UIViewController
-  topLayoutGuide Deprecated

Instance Property

# topLayoutGuide

Indicates the highest vertical extent for your onscreen content, for use with Auto Layout constraints.

iOS 7.0–11.0DeprecatediPadOS 7.0–11.0DeprecatedMac Catalyst 13.1–13.1DeprecatedtvOS 7.0–11.0Deprecated

``` source
@MainActor
var topLayoutGuide: any UILayoutSupport { get }
```

Deprecated

Use the safeAreaLayoutGuide property of UIView instead.

## Discussion

The topLayoutGuide property comes into play when a view controller is frontmost onscreen. It indicates the highest vertical extent for content that you don’t want to appear behind a translucent or transparent UIKit bar (such as a status or navigation bar). This property implements the UILayoutSupport protocol and you can employ it as a constraint item when using the NSLayoutConstraint class.

The value of this property is, specifically, the value of the length property of the object returned when you query this property. This value is constrained by either the view controller or by its enclosing container view controller (such as a navigation or tab bar controller), as follows:

- A view controller **not within** a container view controller constrains this property to indicate the bottom of the status bar, if visible, or else to indicate the top edge of the view controller’s view.

- A view controller **within** a container view controller does not set this property’s value. Instead, the container view controller constrains the value to indicate:

- The bottom of the navigation bar, if a navigation bar is visible

- The bottom of the status bar, if only a status bar is visible

- The top edge of the view controller’s view, if neither a status bar nor navigation bar is visible

If a container navigation controller’s navigation bar is visible and opaque, the navigation controller lays out the frontmost view controller’s view so its top edge abuts the bottom of the navigation bar. In this case, the value of this property is `0`.

Query this property within your implementation of the viewDidLayoutSubviews() method.

When laying out a storyboard scene, the Top Layout Guide object is available in the Interface Builder outline view as a child of the View Controller object. Adding a top layout guide using Interface Builder provides backward compatibility to iOS 6.

As an example of how to programmatically use this property with Auto Layout, say you want to position a control such that its top edge is 20 points below the top layout guide. This scenario applies to any of the scenarios listed above. Use code similar to the following:

```
[button setTranslatesAutoresizingMaskIntoConstraints: NO];
id topGuide = myViewController.topLayoutGuide;
NSDictionary *viewsDictionary = NSDictionaryOfVariableBindings (button, topGuide);
[myViewController.view addConstraints:
    [NSLayoutConstraint constraintsWithVisualFormat: @"V:[topGuide]-20-[button]"
                                                 options: 0
                                                 metrics: nil
                                                   views: viewsDictionary]];
[self.view layoutSubviews]; // You must call this method here or the system raises an exception
```

Important

If you define Auto Layout constraints in a storyboard file as well as programmatically, it is your responsibility to ensure the constraints do not conflict. If they do conflict, the system may throw a runtime exception.

To use a top layout guide without using constraints, obtain the guide’s position relative to the top bound of the containing view. In the case of using a view controller subclass, obtain the numbers you need as follows:

```
- (void) viewDidLayoutSubviews {
    CGRect viewBounds = self.view.bounds;
    CGFloat topBarOffset = self.topLayoutGuide.length;
}
```

In the case of using a view subclass, obtain the numbers you need as follows:

```
- (void) layoutSubviews {
    [super layoutSubviews]; // You must call super here or the system raises an exception
    CGRect bounds = self.bounds;
    CGFloat topBarOffset = myVCReference.topLayoutGuide.length;
}
```

## See Also

### Deprecated properties

var shouldAutorotate: Bool

A Boolean value that indicates whether the view controller’s contents should autorotate.

Deprecated

var previewActionItems: [any UIPreviewActionItem]

The quick actions displayed when a user swipes upward on a 3D Touch preview.

Deprecated

var automaticallyAdjustsScrollViewInsets: Bool

A Boolean value that indicates whether the view controller should automatically adjust its scroll view insets.

Deprecated

var bottomLayoutGuide: any UILayoutSupport

Indicates the lowest vertical extent for your onscreen content, for use with Auto Layout constraints.

Deprecated

var interfaceOrientation: UIInterfaceOrientation

Convenience property that provides the current orientation of the interface, meaningful only if the view controller is taking up the full screen.

Deprecated

var isModalInPopover: Bool

A Boolean value indicating whether the view controller should be presented modally by a popover.

Deprecated

var searchDisplayController: UISearchDisplayController?

The search display controller associated with the view controller.

Deprecated

