*   [WidgetKit](/documentation/widgetkit)
*   Emoji Rangers: Supporting Live Activities, interactivity, and animations

Sample Code

# Emoji Rangers: Supporting Live Activities, interactivity, and animations

Offer Live Activities, controls, animate data updates, and add interactivity to widgets.

[Download](https://docs-assets.developer.apple.com/published/8b262812bc2d/EmojiRangersSupportingLiveActivitiesInteractivityAndAnimations.zip)

iOS 18.0+iPadOS 18.0+watchOS 11.0+Xcode 16.2+

## [Overview](/documentation/WidgetKit/emoji-rangers-supporting-live-activities-interactivity-and-animations#Overview)

Note

This sample code project is associated with WWDC23 sessions 10184: [Meet ActivityKit](https://developer.apple.com/wwdc23/10184/), 10185: [Update live activities with push notifications](https://developer.apple.com/wwdc23/10185/), 10027: [Bring widgets to new places](https://developer.apple.com/wwdc23/10027/), and 10028: [Bring widgets to life](https://developer.apple.com/wwdc23/10028/).

## [See Also](/documentation/WidgetKit/emoji-rangers-supporting-live-activities-interactivity-and-animations#see-also)

### [Widget creation](/documentation/WidgetKit/emoji-rangers-supporting-live-activities-interactivity-and-animations#Widget-creation)

[

Creating a widget extension](/documentation/widgetkit/creating-a-widget-extension)

Display your app’s content in a convenient, informative widget on various devices.

[

Supporting additional widget sizes](/documentation/widgetkit/supporting-additional-widget-sizes)

Offer widgets in additional contexts by adding support for various widget sizes.

[

Creating accessory widgets and watch complications](/documentation/widgetkit/creating-accessory-widgets-and-watch-complications)

Support accessory widgets that appear on the Lock Screen and as complications on Apple Watch.

[`@MainActor @preconcurrency protocol Widget`](/documentation/SwiftUI/Widget)

The configuration and content of a widget to display on the Home screen or in Notification Center.

[`@MainActor @preconcurrency protocol WidgetBundle`](/documentation/SwiftUI/WidgetBundle)

A container used to expose multiple widgets from a single widget extension.

```swift
```swift
```swift
struct StaticConfiguration
```
```

An object describing the content of a widget that has no user-configurable options.
```
```swift
```swift
```swift
enum WidgetFamily
```
```

Values that define the widget’s size and shape.
```