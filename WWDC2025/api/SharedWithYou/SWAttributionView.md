*   [SharedWithYou](/documentation/sharedwithyou)
*   SWAttributionView

Class

# SWAttributionView

A view that displays the sender who shares a highlight and provides related actions.

iOS 16.0+iPadOS 16.0+Mac Catalyst 16.0+macOS 13.0+tvOS 16.0+visionOS 1.0+

```swift
```swift
```swift
```swift
```swift
```swift
```swift

```swift
@[`MainActor`](/documentation/Swift/MainActor)
class SWAttributionView
```

```
```
```
```
```
```
```

## [Mentioned in](/documentation/SharedWithYou/SWAttributionView#mentions)

[

Making your app content shareable](/documentation/sharedwithyou/making-your-app-content-shareable)

## [Overview](/documentation/SharedWithYou/SWAttributionView#overview)

The `SWAttributionView` also allows users to get back to the conversation about the [`SWHighlight`](/documentation/sharedwithyou/swhighlight) content, and other related actions using a [`highlightMenu`](/documentation/sharedwithyou/swattributionview/highlightmenu).

Place an `SWAttributionView` next to the content represented by its `SWHighlight`. The `SWAttributionView` displays the names and avatars within the provided horizontal space.

You can constrain this view’s width anchor or set its frame width to control the maximum width of its contents after which truncation may occur. Don’t constrain the view’s height, as the height is dependent on the [`preferredContentSizeCategory`](/documentation/UIKit/UIApplication/preferredContentSizeCategory), and the resulting font size. To provide enough vertical space around this view, reference its [`heightAnchor`](/documentation/UIKit/UIView/heightAnchor) when using Auto Layout, or its [`intrinsicContentSize`](/documentation/UIKit/UIView/intrinsicContentSize) when using manual layout.

## [Topics](/documentation/SharedWithYou/SWAttributionView#topics)

### [Customizing highlights](/documentation/SharedWithYou/SWAttributionView#Customizing-highlights)

```swift
```swift
```swift
```swift
var backgroundStyle: SWAttributionView.BackgroundStyle
```
```

The background style of the child view that contains names and avatars.
```
```swift
```swift
```swift
var displayContext: SWAttributionView.DisplayContext
```
```

The context for the content the system displays with this view.
```
```swift
```swift
```swift
var highlight: SWHighlight?
```
```

The highlight you use to display this attribution.
```
```swift
```swift
```swift
var highlightMenu: UIMenu
```
```

A menu with a list of system actions specific to this hightlight.
```
```swift
```swift
```swift
var horizontalAlignment: SWAttributionView.HorizontalAlignment
```
```

The horizontal alignment of the view.
```
```swift
```swift
```swift
var menuTitleForHideAction: String?
```
```

A localized string the system uses as a custom title for the hide menu item.
```
```swift
```swift
```swift
var preferredMaxLayoutWidth: CGFloat
```
```

A width the system uses to constrain the view contents.
```
```swift
```swift
```swift
var supplementalMenu: UIMenu?
```
```

A supplemental menu to augment the attribution view’s existing menu.
```
```

### [Customizing the view](/documentation/SharedWithYou/SWAttributionView#Customizing-the-view)

```swift
```swift
```swift
```swift
enum BackgroundStyle
```
```

The background styling of the attribution view’s contents.
```
```swift
```swift
```swift
enum DisplayContext
```
```

The context for the content that influences the ranking of this view’s highlight.
```
```swift
```swift
```swift
enum HorizontalAlignment
```
```

The horizontal alignment of attribution view’s contents.
```
```

## [Relationships](/documentation/SharedWithYou/SWAttributionView#relationships)

### [Inherits From](/documentation/SharedWithYou/SWAttributionView#inherits-from)

*   [`NSView`](/documentation/AppKit/NSView)
*   [`UIView`](/documentation/UIKit/UIView)

### [Conforms To](/documentation/SharedWithYou/SWAttributionView#conforms-to)

*   [`CALayerDelegate`](/documentation/QuartzCore/CALayerDelegate)
*   [`CVarArg`](/documentation/Swift/CVarArg)
*   [`CustomDebugStringConvertible`](/documentation/Swift/CustomDebugStringConvertible)
*   [`CustomStringConvertible`](/documentation/Swift/CustomStringConvertible)
*   [`Equatable`](/documentation/Swift/Equatable)
*   [`Hashable`](/documentation/Swift/Hashable)
*   [`NSAccessibilityElementProtocol`](/documentation/AppKit/NSAccessibilityElementProtocol)
*   [`NSAccessibilityProtocol`](/documentation/AppKit/NSAccessibilityProtocol)
*   [`NSAnimatablePropertyContainer`](/documentation/AppKit/NSAnimatablePropertyContainer)
*   [`NSAppearanceCustomization`](/documentation/AppKit/NSAppearanceCustomization)
*   [`NSCoding`](/documentation/Foundation/NSCoding)
*   [`NSDraggingDestination`](/documentation/AppKit/NSDraggingDestination)
*   [`NSObjectProtocol`](/documentation/ObjectiveC/NSObjectProtocol)
*   [`NSStandardKeyBindingResponding`](/documentation/AppKit/NSStandardKeyBindingResponding)
*   [`NSTouchBarProvider`](/documentation/AppKit/NSTouchBarProvider)
*   [`NSUserActivityRestoring`](/documentation/AppKit/NSUserActivityRestoring)
*   [`NSUserInterfaceItemIdentification`](/documentation/AppKit/NSUserInterfaceItemIdentification)
*   [`Sendable`](/documentation/Swift/Sendable)
*   [`SendableMetatype`](/documentation/Swift/SendableMetatype)
*   [`UIAccessibilityIdentification`](/documentation/UIKit/UIAccessibilityIdentification)
*   [`UIActivityItemsConfigurationProviding`](/documentation/UIKit/UIActivityItemsConfigurationProviding)
*   [`UIAppearance`](/documentation/UIKit/UIAppearance)
*   [`UIAppearanceContainer`](/documentation/UIKit/UIAppearanceContainer)
*   [`UICoordinateSpace`](/documentation/UIKit/UICoordinateSpace)
*   [`UIDynamicItem`](/documentation/UIKit/UIDynamicItem)
*   [`UIFocusEnvironment`](/documentation/UIKit/UIFocusEnvironment)
*   [`UIFocusItem`](/documentation/UIKit/UIFocusItem)
*   [`UIFocusItemContainer`](/documentation/UIKit/UIFocusItemContainer)
*   [`UILargeContentViewerItem`](/documentation/UIKit/UILargeContentViewerItem)
*   [`UIPasteConfigurationSupporting`](/documentation/UIKit/UIPasteConfigurationSupporting)
*   [`UIPopoverPresentationControllerSourceItem`](/documentation/UIKit/UIPopoverPresentationControllerSourceItem)
*   [`UIResponderStandardEditActions`](/documentation/UIKit/UIResponderStandardEditActions)
*   [`UITraitChangeObservable`](/documentation/UIKit/UITraitChangeObservable-67e94)
*   [`UITraitEnvironment`](/documentation/UIKit/UITraitEnvironment)
*   [`UIUserActivityRestoring`](/documentation/UIKit/UIUserActivityRestoring)