*   [UIKit](/documentation/uikit)
*   UISheetPresentationController

Class

# UISheetPresentationController

A presentation controller that manages the appearance and behavior of a sheet.

iOS 15.0+iPadOS 15.0+Mac Catalyst 15.0+visionOS 1.0+

```swift
```swift
```swift
```swift
```swift
```swift
```swift

```swift
@[`MainActor`](/documentation/Swift/MainActor)
class UISheetPresentationController
```

```
```
```
```
```
```
```

## [Overview](/documentation/UIKit/UISheetPresentationController#overview)

[`UISheetPresentationController`](/documentation/uikit/uisheetpresentationcontroller) lets you present your view controller as a sheet. Before you present your view controller, configure the sheet presentation controller in its [`sheetPresentationController`](/documentation/uikit/uiviewcontroller/sheetpresentationcontroller) property with the behavior and appearance you want for your sheet.

```swift

```swift
// In a subclass of UIViewController, customize and present the sheet.
```swift
```swift
func showMyViewControllerInACustomizedSheet() {
```
```
    let viewControllerToPresent = MyViewController()
    if let sheet = viewControllerToPresent.sheetPresentationController {
        sheet.detents = [.medium(), .large()]
        sheet.largestUndimmedDetentIdentifier = .medium
        sheet.prefersScrollingExpandsWhenScrolledToEdge = false
        sheet.prefersEdgeAttachedInCompactHeight = true
        sheet.widthFollowsPreferredContentSizeWhenEdgeAttached = true
    }
    present(viewControllerToPresent, animated: true, completion: nil)
}
```

```

Sheet presentation controllers specify a sheet’s size based on a _detent_, a height where a sheet naturally rests. Detents allow a sheet to resize from one edge of its fully expanded frame while the other three edges remain fixed. You specify the detents that a sheet supports using [`detents`](/documentation/uikit/uisheetpresentationcontroller/detents), and monitor its most recently selected detent using [`selectedDetentIdentifier`](/documentation/uikit/uisheetpresentationcontroller/selecteddetentidentifier).

Related Sessions from WWDC21

Session 10063: [Customize and Resize Sheets in UIKit](https://developer.apple.com/wwdc21/10063)

Session 10068: [What’s new in UIKit](https://developer.apple.com/videos/play/wwdc2022/10068)

## [Topics](/documentation/UIKit/UISheetPresentationController#topics)

### [Specifying the height](/documentation/UIKit/UISheetPresentationController#Specifying-the-height)

```swift
```swift
```swift
```swift
var detents: [UISheetPresentationController.Detent]
```
```

The array of heights where a sheet can rest.
```
```swift
```swift
```swift
var selectedDetentIdentifier: UISheetPresentationController.Detent.Identifier?
```
```

The identifier of the most recently selected detent.
```
```swift
```swift
```swift
class Detent
```
```

An object that represents a height where a sheet naturally rests.
```
```

### [Managing the delegate](/documentation/UIKit/UISheetPresentationController#Managing-the-delegate)

```swift
```swift
```swift
```swift
var delegate: (any UISheetPresentationControllerDelegate)?
```
```

The delegate of the sheet presentation controller.
```
```swift
```swift
```swift
protocol UISheetPresentationControllerDelegate
```
```

The interface that an object implements to respond to size changes in a sheet presentation controller.
```
```

### [Managing user interaction](/documentation/UIKit/UISheetPresentationController#Managing-user-interaction)

```swift
```swift
```swift
```swift
var largestUndimmedDetentIdentifier: UISheetPresentationController.Detent.Identifier?
```
```

The largest detent that doesn’t dim the view underneath the sheet.
```
```swift
```swift
```swift
var prefersScrollingExpandsWhenScrolledToEdge: Bool
```
```

A Boolean value that determines whether scrolling expands the sheet to a larger detent.
```
```

### [Managing the appearance](/documentation/UIKit/UISheetPresentationController#Managing-the-appearance)

```swift
```swift
```swift
```swift
var prefersGrabberVisible: Bool
```
```

A Boolean value that determines whether the sheet shows a grabber at the top.
```
```swift
```swift
```swift
var prefersPageSizing: Bool
```
```

A Boolean value that indicates whether the sheet sizes itself for readable content.
```
```swift
```swift
```swift
var prefersEdgeAttachedInCompactHeight: Bool
```
```

A Boolean value that determines whether the sheet attaches to the bottom edge of the screen in a compact-height size class.
```
```swift
```swift
```swift
var widthFollowsPreferredContentSizeWhenEdgeAttached: Bool
```
```

A Boolean value that determines whether the sheet’s width matches its view controller’s preferred content size.
```
```swift
```swift
```swift
var preferredCornerRadius: CGFloat?
```
```

The corner radius that the sheet attempts to present with.
```
```

### [Customizing the position](/documentation/UIKit/UISheetPresentationController#Customizing-the-position)

```swift
```swift
```swift
```swift
var sourceView: UIView?
```
```

The view that the sheet centers itself over.
```
```

### [Working with custom detents](/documentation/UIKit/UISheetPresentationController#Working-with-custom-detents)

```swift
```swift
```swift
```swift
func invalidateDetents()
```
```

Notifies the sheet to re-evaluate its detent value in the next layout pass.
```
```

### [Animating changes to the sheet](/documentation/UIKit/UISheetPresentationController#Animating-changes-to-the-sheet)

```swift
```swift
```swift
```swift
func animateChanges(() -> Void)
```
```

Animates the UI changes to the sheet’s properties.
```
```

## [Relationships](/documentation/UIKit/UISheetPresentationController#relationships)

### [Inherits From](/documentation/UIKit/UISheetPresentationController#inherits-from)

*   [`UIPresentationController`](/documentation/uikit/uipresentationcontroller)

### [Conforms To](/documentation/UIKit/UISheetPresentationController#conforms-to)

*   [`CVarArg`](/documentation/Swift/CVarArg)
*   [`CustomDebugStringConvertible`](/documentation/Swift/CustomDebugStringConvertible)
*   [`CustomStringConvertible`](/documentation/Swift/CustomStringConvertible)
*   [`Equatable`](/documentation/Swift/Equatable)
*   [`Hashable`](/documentation/Swift/Hashable)
*   [`NSObjectProtocol`](/documentation/ObjectiveC/NSObjectProtocol)
*   [`Sendable`](/documentation/Swift/Sendable)
*   [`SendableMetatype`](/documentation/Swift/SendableMetatype)
*   [`UIAppearanceContainer`](/documentation/uikit/uiappearancecontainer)
*   [`UIContentContainer`](/documentation/uikit/uicontentcontainer)
*   [`UIFocusEnvironment`](/documentation/uikit/uifocusenvironment)
*   [`UITraitChangeObservable`](/documentation/uikit/uitraitchangeobservable-67e94)
*   [`UITraitEnvironment`](/documentation/uikit/uitraitenvironment)

## [See Also](/documentation/UIKit/UISheetPresentationController#see-also)

### [Presentation management](/documentation/UIKit/UISheetPresentationController#Presentation-management)

[

Disabling the pull-down gesture for a sheet](/documentation/uikit/disabling-the-pull-down-gesture-for-a-sheet)

Ensure a positive user experience when presenting a view controller as a sheet.

```swift
```swift
```swift
class UIPresentationController
```
```

An object that manages the transition animations and the presentation of view controllers onscreen.
```