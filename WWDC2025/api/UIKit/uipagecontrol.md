*   [UIKit](/documentation/uikit)
*   UIPageControl

Class

# UIPageControl

A control that displays a horizontal series of dots, each of which corresponds to a page in the app’s document or other data-model entity.

iOS 2.0+iPadOS 2.0+Mac Catalyst 13.1+tvOSvisionOS 1.0+

```swift
```swift
```swift
```swift
```swift
```swift
```swift

```swift
@[`MainActor`](/documentation/Swift/MainActor)
class UIPageControl
```

```
```
```
```
```
```
```

## [Mentioned in](/documentation/UIKit/UIPageControl#mentions)

[

Attaching gesture recognizers to UIKit controls](/documentation/uikit/attaching-gesture-recognizers-to-uikit-controls)

[

Choosing a user interface idiom for your Mac app](/documentation/uikit/choosing-a-user-interface-idiom-for-your-mac-app)

## [Overview](/documentation/UIKit/UIPageControl#overview)

For an example of a page control, see the Weather app when it’s configured to display information for more than one location.

When a user taps a page control to move to the next or previous page, the control sends the [`valueChanged`](/documentation/uikit/uicontrol/event/valuechanged) event for handling by the delegate. The delegate can then evaluate the [`currentPage`](/documentation/uikit/uipagecontrol/currentpage) property to determine the page to display. The page control advances only one page in either direction. The currently viewed page is indicated by a white dot. Depending on the device, a certain number of dots are displayed on the screen before they’re clipped.

## [Topics](/documentation/UIKit/UIPageControl#topics)

### [Managing pages](/documentation/UIKit/UIPageControl#Managing-pages)

```swift
```swift
```swift
```swift
var currentPage: Int
```
```

The current page, shown by the page control as a white dot.
```
```swift
```swift
```swift
var numberOfPages: Int
```
```

The number of pages the receiver shows (as dots).
```
```swift
```swift
```swift
var hidesForSinglePage: Bool
```
```

A Boolean value that controls whether the page control is hidden when there is only one page.
```
```swift
```swift
```swift
var defersCurrentPageDisplay: Bool
```
```

A Boolean value that controls when the current page is displayed.

Deprecated
```
```swift
```swift
```swift
func updateCurrentPageDisplay()
```
```

Updates the page indicator to the current page.

Deprecated
```
```

### [Coloring the page indicator](/documentation/UIKit/UIPageControl#Coloring-the-page-indicator)

```swift
```swift
```swift
```swift
var pageIndicatorTintColor: UIColor?
```
```

The tint color to apply to the page indicator.
```
```swift
```swift
```swift
var currentPageIndicatorTintColor: UIColor?
```
```

The tint color to apply to the current page indicator.
```
```

### [Managing the indicator images](/documentation/UIKit/UIPageControl#Managing-the-indicator-images)

```swift
```swift
```swift
```swift
var preferredIndicatorImage: UIImage?
```
```

The preferred image for indicators.
```
```swift
```swift
```swift
func indicatorImage(forPage: Int) -> UIImage?
```
```

Returns the override image for the indicator of the specified page.
```
```swift
```swift
```swift
func setIndicatorImage(UIImage?, forPage: Int)
```
```

Registers an override image for the indicator of the specified page.
```
```swift
```swift
```swift
var preferredCurrentPageIndicatorImage: UIImage?
```
```

The preferred image for the current page indicator.
```
```swift
```swift
```swift
func currentPageIndicatorImage(forPage: Int) -> UIImage?
```
```

Returns the override image for the current page indicator of the specified page.
```
```swift
```swift
```swift
func setCurrentPageIndicatorImage(UIImage?, forPage: Int)
```
```

Registers an override image for the current page indicator of the specified page.
```
```

### [Customizing the layout direction](/documentation/UIKit/UIPageControl#Customizing-the-layout-direction)

```swift
```swift
```swift
```swift
var direction: UIPageControl.Direction
```
```

The layout direction of the page indicators.
```
```swift
```swift
```swift
enum Direction
```
```

Decribes the layout direction of a page control’s indicators.
```
```

### [Customizing the background style](/documentation/UIKit/UIPageControl#Customizing-the-background-style)

```swift
```swift
```swift
```swift
var backgroundStyle: UIPageControl.BackgroundStyle
```
```

The preferred background style.
```
```swift
```swift
```swift
enum BackgroundStyle
```
```

Constants that define the background styles of the page control.
```
```

### [Customizing the interaction state](/documentation/UIKit/UIPageControl#Customizing-the-interaction-state)

```swift
```swift
```swift
```swift
var allowsContinuousInteraction: Bool
```
```

A Boolean value that determines whether the page control allows continuous interaction.
```
```swift
```swift
```swift
var interactionState: UIPageControl.InteractionState
```
```

The interaction state when the current page changes.
```
```swift
```swift
```swift
enum InteractionState
```
```

Constants that define the interaction states of the page control.
```
```

### [Calculating the control size](/documentation/UIKit/UIPageControl#Calculating-the-control-size)

```swift
```swift
```swift
```swift
func size(forNumberOfPages: Int) -> CGSize
```
```

Returns the size the receiver’s bounds should be to accommodate the given number of pages.
```
```

### [Configuring page progress](/documentation/UIKit/UIPageControl#Configuring-page-progress)

```swift
```swift
```swift
```swift
var progress: UIPageControlProgress?
```
```
```
```swift
```swift
```swift
class UIPageControlProgress
```
```
```
```swift
```swift
```swift
class UIPageControlTimerProgress
```
```
```
```swift
```swift
```swift
protocol UIPageControlProgressDelegate
```
```
```
```swift
```swift
```swift
protocol UIPageControlTimerProgressDelegate
```
```
```
```

## [Relationships](/documentation/UIKit/UIPageControl#relationships)

### [Inherits From](/documentation/UIKit/UIPageControl#inherits-from)

*   [`UIControl`](/documentation/uikit/uicontrol)

### [Conforms To](/documentation/UIKit/UIPageControl#conforms-to)

*   [`CALayerDelegate`](/documentation/QuartzCore/CALayerDelegate)
*   [`CVarArg`](/documentation/Swift/CVarArg)
*   [`CustomDebugStringConvertible`](/documentation/Swift/CustomDebugStringConvertible)
*   [`CustomStringConvertible`](/documentation/Swift/CustomStringConvertible)
*   [`Equatable`](/documentation/Swift/Equatable)
*   [`Hashable`](/documentation/Swift/Hashable)
*   [`NSCoding`](/documentation/Foundation/NSCoding)
*   [`NSObjectProtocol`](/documentation/ObjectiveC/NSObjectProtocol)
*   [`NSTouchBarProvider`](/documentation/AppKit/NSTouchBarProvider)
*   [`Sendable`](/documentation/Swift/Sendable)
*   [`SendableMetatype`](/documentation/Swift/SendableMetatype)
*   [`UIAccessibilityIdentification`](/documentation/uikit/uiaccessibilityidentification)
*   [`UIActivityItemsConfigurationProviding`](/documentation/uikit/uiactivityitemsconfigurationproviding)
*   [`UIAppearance`](/documentation/uikit/uiappearance)
*   [`UIAppearanceContainer`](/documentation/uikit/uiappearancecontainer)
*   [`UIContextMenuInteractionDelegate`](/documentation/uikit/uicontextmenuinteractiondelegate)
*   [`UICoordinateSpace`](/documentation/uikit/uicoordinatespace)
*   [`UIDynamicItem`](/documentation/uikit/uidynamicitem)
*   [`UIFocusEnvironment`](/documentation/uikit/uifocusenvironment)
*   [`UIFocusItem`](/documentation/uikit/uifocusitem)
*   [`UIFocusItemContainer`](/documentation/uikit/uifocusitemcontainer)
*   [`UILargeContentViewerItem`](/documentation/uikit/uilargecontentvieweritem)
*   [`UIPasteConfigurationSupporting`](/documentation/uikit/uipasteconfigurationsupporting)
*   [`UIPopoverPresentationControllerSourceItem`](/documentation/uikit/uipopoverpresentationcontrollersourceitem)
*   [`UIResponderStandardEditActions`](/documentation/uikit/uiresponderstandardeditactions)
*   [`UITraitChangeObservable`](/documentation/uikit/uitraitchangeobservable-67e94)
*   [`UITraitEnvironment`](/documentation/uikit/uitraitenvironment)
*   [`UIUserActivityRestoring`](/documentation/uikit/uiuseractivityrestoring)

## [See Also](/documentation/UIKit/UIPageControl#see-also)

### [Controls](/documentation/UIKit/UIPageControl#Controls)

[

Responding to control-based events using target-action](/documentation/uikit/responding-to-control-based-events-using-target-action)

Handle user input by connecting buttons, sliders, and other controls to your app’s code using the target-action design pattern.

```swift
```swift
```swift
class UIControl
```
```

The base class for controls, which are visual elements that convey a specific action or intention in response to user interactions.
```
```swift
```swift
```swift
class UIButton
```
```

A control that executes your custom code in response to user interactions.
```
```swift
```swift
```swift
class UIColorWell
```
```

A control that displays a color picker.
```
```swift
```swift
```swift
class UIDatePicker
```
```

A control for inputting date and time values.
```
```swift
```swift
```swift
class UISegmentedControl
```
```

A horizontal control that consists of multiple segments, each segment functioning as a discrete button.
```
```swift
```swift
```swift
class UISlider
```
```

A control for selecting a single value from a continuous range of values.
```
```swift
```swift
```swift
class UIStepper
```
```

A control for incrementing or decrementing a value.
```
```swift
```swift
```swift
class UISwitch
```
```

A control that offers a binary choice, such as on/off.
```