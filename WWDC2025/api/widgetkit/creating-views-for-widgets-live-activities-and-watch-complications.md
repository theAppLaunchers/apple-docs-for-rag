*   [WidgetKit](/documentation/widgetkit)
*   Creating views for widgets, Live Activities, and watch complications

Article

# Creating views for widgets, Live Activities, and watch complications

Implement glanceable views with WidgetKit and SwiftUI.

## [Overview](/documentation/WidgetKit/Creating-views-for-widgets-Live-Activities-and-watch-complications#Overview)

SwiftUI and WidgetKit power widgets, Live Activities, and watch complications. Because they use the same technology and share design similarities, plan your WidgetKit adoption before you start creating these features. Start simple and add complexity later; for example, start by adding a widget extension as described in [Creating a widget extension](/documentation/widgetkit/creating-a-widget-extension) and support one widget size. Spend time to make sure it offers a focused, glanceable experience. Then, add support for additional widget sizes and features like configurability, animations, and interactivity.

Related session from WWDC23

[Session 10027: Bring widgets to new places](https://developer.apple.com/videos/play/wwdc2023/10027)

If you’re new to using WidgetKit, see [Developing a WidgetKit strategy](/documentation/widgetkit/developing-a-widgetkit-strategy).

### [Use system font styles](/documentation/WidgetKit/Creating-views-for-widgets-Live-Activities-and-watch-complications#Use-system-font-styles)

Widgets, Live Activities, and watch complications appear adjacent to other widgets or complications. As a result, a consistent look for your content that fits in well with the other elements needs to be a priority. To achieve a consistent look for your widgets and complications, use system fonts, default font parameters, and the following font styles:

*   [`Font.TextStyle.headline`](/documentation/SwiftUI/Font/TextStyle/headline)
    
*   [`Font.TextStyle.title`](/documentation/SwiftUI/Font/TextStyle/title)
    
*   [`Font.TextStyle.body`](/documentation/SwiftUI/Font/TextStyle/body)
    
*   [`Font.TextStyle.caption`](/documentation/SwiftUI/Font/TextStyle/caption)
    

### [Make sure text fits the available space](/documentation/WidgetKit/Creating-views-for-widgets-Live-Activities-and-watch-complications#Make-sure-text-fits-the-available-space)

Widgets and watch complications offer limited space for content — especially on the Lock Screen or on Apple Watch. Give careful consideration to the amount of text you display. For example, say you support the [`WidgetFamily.accessoryInline`](/documentation/widgetkit/widgetfamily/accessoryinline) widget. It can include an image and text. However, the amount of displayable characters varies depending on the context where the widget appears. On Apple Watch, the size of the inline complication varies depending on the watch face. Include it in a [`ViewThatFits`](/documentation/SwiftUI/ViewThatFits) view to make sure text always fits the available space.

Note

Test your widgets with every language you support, especially if you support languages that commonly have words with a lot of characters, such as German.

### [Use content margins instead of safe areas](/documentation/WidgetKit/Creating-views-for-widgets-Live-Activities-and-watch-complications#Use-content-margins-instead-of-safe-areas)

watchOS 9, iOS 16, iPadOS 16, macOS 13, and earlier use system-defined safe areas to keep content from getting too close to the edge of the widget, complication, or Live Activity. You likely don’t change the safe areas that the system defines. However, you might use the [`ignoresSafeArea(_:edges:)`](/documentation/SwiftUI/View/ignoresSafeArea\(_:edges:\)) view modifier to extend content farther than the safe area.

WidgetKit complications, and Live Activities use content margins instead of safe areas. As a result, `ignoresSafeArea(_:edges:)` has no effect. Instead, use the [`contentMarginsDisabled()`](/documentation/SwiftUI/WidgetConfiguration/contentMarginsDisabled\(\)) view modifier to define custom content margins.

If you use `ignoresSafeArea(_:edges:)`, follow these steps:

1.  Add the `contentMarginsDisabled()` view modifier to your widget configuration.
    
2.  For any content that you intend to remain inside system-defined content margins, make use of [`padding(_:)`](/documentation/SwiftUI/View/padding\(_:\)) as needed.
    

Tip

To access the system’s default content margins for an environment, use the [`widgetContentMargins`](/documentation/SwiftUI/EnvironmentValues/widgetContentMargins) environment variable.

## [See Also](/documentation/WidgetKit/Creating-views-for-widgets-Live-Activities-and-watch-complications#see-also)

### [Presentation](/documentation/WidgetKit/Creating-views-for-widgets-Live-Activities-and-watch-complications#Presentation)

[

Preparing widgets for additional platforms, contexts, and appearances](/documentation/widgetkit/preparing-widgets-for-additional-contexts-and-appearances)

Create widgets that support additional platforms and adapt to their context.

[

Displaying the right widget background](/documentation/widgetkit/displaying-the-right-widget-background)

Group your widget’s background views and mark them as removable to ensure your widget appears correctly for each context and platform.

[

Optimizing your widget for accented rendering mode and Liquid Glass](/documentation/widgetkit/optimizing-your-widget-for-accented-rendering-mode-and-liquid-glass)

Make your widget feel at home on Apple platforms and Liquid Glass by using accented rendering mode.

[

Adding StandBy and CarPlay support to your widget](/documentation/widgetkit/adding-standby-and-carplay-support-to-your-widget)

Ensure that your small system family widget works well in StandBy and CarPlay.

[

API Reference

SwiftUI views for widgets](/documentation/widgetkit/swiftui-views)

Present your app’s content in widgets with SwiftUI views.

[

Introducing SwiftUI](/tutorials/SwiftUI)

SwiftUI is a modern way to declare user interfaces for any Apple platform. Create beautiful, dynamic apps faster than ever before.

```swift
```swift
```swift
struct WidgetRenderingMode
```
```

Constants that indicate the rendering mode for a widget.
```
```swift
```swift
```swift
struct WidgetAccentedRenderingMode
```
```

Constants that indicate the rendering mode for an `Image` in when displayed in a widget in [`accented`](/documentation/widgetkit/widgetrenderingmode/accented) mode.
```
```swift
```swift
```swift
struct AccessoryWidgetBackground
```
```

An adaptive background view that provides a standard appearance based on the the widget’s environment.
```
```swift
```swift
```swift
struct WidgetLocation
```
```

Values that indicate different widget locations.
```