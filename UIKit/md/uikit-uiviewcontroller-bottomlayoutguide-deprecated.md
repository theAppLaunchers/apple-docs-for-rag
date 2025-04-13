

- UIKit
- UIViewController
-  bottomLayoutGuide Deprecated

Instance Property

# bottomLayoutGuide

Indicates the lowest vertical extent for your onscreen content, for use with Auto Layout constraints.

iOS 7.0–11.0DeprecatediPadOS 7.0–11.0DeprecatedMac Catalyst 13.1–13.1DeprecatedtvOSDeprecated

``` source
@MainActor
var bottomLayoutGuide: any UILayoutSupport { get }
```

Deprecated

Use the safeAreaLayoutGuide property of UIView instead.

## Discussion

The bottomLayoutGuide property comes into play when a view controller is frontmost onscreen. It indicates the lowest vertical extent for content that you don’t want to appear behind a translucent or transparent UIKit bar (such as a tab bar or toolbar). This property implements the UILayoutSupport protocol and you can employ it as a constraint item when using the NSLayoutConstraint class.

The value of this property is, specifically, the value of the length property of the object returned when you query this property. This value is constrained by either the view controller or by its enclosing container view controller (such as a navigation or tab bar controller), as follows:

- A view controller **not within** a container view controller constrains this property to indicate the top of the tab bar or toolbar, if one of these is visible, or else to indicate the bottom edge of the view controller’s view.

- A view controller **within** a container view controller does not set this property’s value. Instead, the container view controller constrains the value to indicate the top of the tab bar or toolbar, if one of these is visible, or else to indicate the bottom edge of the view controller’s view.

If a container view controller’s toolbar or tab bar is visible and opaque, the container lays out the frontmost view controller’s view so its bottom edge abuts the top of the bar. In this case, the value of this property is 0.

Query this property within your implementation of the viewDidLayoutSubviews() method.

When laying out a storyboard scene, the Bottom Layout Guide object is available in the Interface Builder outline view as a child of the View Controller object. Adding a bottom layout guide using Interface Builder provides backward layout compatibility to iOS 6.

As an example of how to programmatically use this property with Auto Layout, say you want to position a control such that its bottom edge is 20 points above the bottom layout guide. This scenario applies to any of the scenarios listed above. Use code similar to the following:

```
[button setTranslatesAutoresizingMaskIntoConstraints: NO];
id bottomGuide = myViewController.bottomLayoutGuide;
NSDictionary *viewsDictionary = NSDictionaryOfVariableBindings (button, bottomGuide);
[myViewController.view addConstraints:
    [NSLayoutConstraint constraintsWithVisualFormat: @"V: [button]-20-[bottomGuide]"
                                                 options: 0
                                                 metrics: nil
                                                   views: viewsDictionary]];
[self.view layoutSubviews]; // You must call this method here or the system raises an exception
```

Important

If you define Auto Layout constraints in a storyboard file as well as programmatically, it is your responsibility to ensure the constraints do not conflict. If they do conflict, the system may throw a runtime exception.

To use a bottom layout guide without using constraints, obtain the guide’s position relative to the bottom bound of the containing view. In the case of using a view controller subclass, obtain the numbers you need as follows:

```
- (void) viewDidLayoutSubviews {
    CGRect viewBounds = self.view.bounds;
    CGFloat bottomBarOffset = self.bottomLayoutGuide.length;
}
```

In the case of using a view subclass, obtain the numbers you need as follows:

```
- (void) layoutSubviews {
    [super layoutSubviews]; // You must call super here or the system raises an exception
    CGRect bounds = self.bounds;
    CGFloat bottomBarOffset = myVCReference.bottomLayoutGuide.length;
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

var interfaceOrientation: UIInterfaceOrientation

Convenience property that provides the current orientation of the interface, meaningful only if the view controller is taking up the full screen.

Deprecated

var isModalInPopover: Bool

A Boolean value indicating whether the view controller should be presented modally by a popover.

Deprecated

var searchDisplayController: UISearchDisplayController?

The search display controller associated with the view controller.

Deprecated

var topLayoutGuide: any UILayoutSupport

Indicates the highest vertical extent for your onscreen content, for use with Auto Layout constraints.

Deprecated

