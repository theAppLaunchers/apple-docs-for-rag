*   [WidgetKit](/documentation/widgetkit)
*   Preparing widgets for additional platforms, contexts, and appearances

Article

# Preparing widgets for additional platforms, contexts, and appearances

Create widgets that support additional platforms and adapt to their context.

## [Overview](/documentation/WidgetKit/Preparing-widgets-for-additional-contexts-and-appearances#Overview)

Widgets change their appearance to best fit their context. For example, widgets on the Home Screen, Today View, and on Mac use accented colors and a clear glass presentation with a specific tint color, or they appear in a full color rendering. In CarPlay, small widgets appear scaled up and in full color, while Lock Screen widgets and WidgetKit complications use more restrained colors because they’re smaller, always visible, and support tinted modes for each platform. Because all widgets appear in more than one context, make sure your widgets and their SwiftUI views support all applicable rendering modes.

WidgetKit uses three different rendering modes:

[`accented`](/documentation/widgetkit/widgetrenderingmode/accented)

Divides the widget’s view hierarchy into an accent group and a primary group, and then applies a solid color to each group. Use the [`widgetAccentable(_:)`](/documentation/SwiftUI/View/widgetAccentable\(_:\)) view modifier to group views into the accent group. To learn more about using the `accented` rendering mode and making your widget fit the system’s look across Apple platforms, refer to [Optimizing your widget for accented rendering mode and Liquid Glass](/documentation/widgetkit/optimizing-your-widget-for-accented-rendering-mode-and-liquid-glass).

[`vibrant`](/documentation/widgetkit/widgetrenderingmode/vibrant)

Desaturates text, images, and gauges into monochrome and creates a vibrant effect by coloring your content appropriately for the Lock Screen background or a macOS desktop. Note that people can also color the Lock Screen to a colored tint and WidgetKit uses a red tint for widgets that appear on iPhone in StandBy in low-light conditions.

[`fullColor`](/documentation/widgetkit/widgetrenderingmode/fullcolor)

Doesn’t change the color of your complication’s views in this rendering mode. Use gradients and full-color images, text, and gauges.

The following table shows the rendering modes for each widget you need to support:

Widget size

[`fullColor`](/documentation/widgetkit/widgetrenderingmode/fullcolor)

[`accented`](/documentation/widgetkit/widgetrenderingmode/accented)

[`vibrant`](/documentation/widgetkit/widgetrenderingmode/vibrant)

[`WidgetFamily.systemSmall`](/documentation/widgetkit/widgetfamily/systemsmall)

Yes

Yes

Yes

[`WidgetFamily.systemMedium`](/documentation/widgetkit/widgetfamily/systemmedium)

Yes

Yes

Yes

[`WidgetFamily.systemLarge`](/documentation/widgetkit/widgetfamily/systemlarge)

Yes

Yes

Yes

[`WidgetFamily.systemExtraLarge`](/documentation/widgetkit/widgetfamily/systemextralarge)

Yes

Yes

Yes

[`WidgetFamily.systemExtraLargePortrait`](/documentation/widgetkit/widgetfamily/systemextralargeportrait)

Yes

Yes

Yes

[`WidgetFamily.accessoryCircular`](/documentation/widgetkit/widgetfamily/accessorycircular)

No

Yes

Yes

[`WidgetFamily.accessoryCorner`](/documentation/widgetkit/widgetfamily/accessorycorner)

No

Yes

Yes

[`WidgetFamily.accessoryRectangular`](/documentation/widgetkit/widgetfamily/accessoryrectangular)

Yes

Yes

Yes

[`WidgetFamily.accessoryInline`](/documentation/widgetkit/widgetfamily/accessoryinline)

No

Yes

Yes

Note

For design guidance, see [Human Interface Guidelines > Complications](https://developer.apple.com/design/human-interface-guidelines/complications) and [Human Interface Guidelines > Widgets](https://developer.apple.com/design/human-interface-guidelines/widgets).

In your code, read the [`widgetRenderingMode`](/documentation/SwiftUI/EnvironmentValues/widgetRenderingMode) environment variable to create SwiftUI views for each applicable rendering mode, as shown in the following example:

```swift

```swift
// ...
@Environment(\.widgetRenderingMode) var renderingMode
```swift
```swift
var body: some View {
```
```
   ZStack {
       switch renderingMode {
       case .fullColor:
           // Create views for full-color widgets and watch complications.
       case .accented:
           // Create views and group applicable views in the accented group.
           VStack {
               // ...
           }
           .widgetAccentable()
           // Additional views that you don't group in the accented group.
       case .vibrant:
           // Create views for Lock Screen widgets on iPhone and iPad.
   }
}
```

```

### [Make your background views removable](/documentation/WidgetKit/Preparing-widgets-for-additional-contexts-and-appearances#Make-your-background-views-removable)

In many contexts, the system removes your widget’s background views to match the system appearance. To control which components of your widget the system removes, group them into background containers and mark them as removable. For more information, refer to [Displaying the right widget background](/documentation/widgetkit/displaying-the-right-widget-background).

### [Support Always On](/documentation/WidgetKit/Preparing-widgets-for-additional-contexts-and-appearances#Support-Always-On)

If you create accessory widgets and WidgetKit complications, make sure to use SwiftUI’s [`isLuminanceReduced`](/documentation/SwiftUI/EnvironmentValues/isLuminanceReduced) environment variable to detect Always On and color your views to look great with reduced luminance. For design guidance, see [Human Interface Guidelines > Always On](https://developer.apple.com/design/human-interface-guidelines/always-on) and [Human Interface Guidelines > Widgets](https://developer.apple.com/design/human-interface-guidelines/widgets).

### [Update your small widget to support StandBy and CarPlay](/documentation/WidgetKit/Preparing-widgets-for-additional-contexts-and-appearances#Update-your-small-widget-to-support-StandBy-and-CarPlay)

On iPhone in StandBy, the Lock Screen shows two widgets side by side on a dark background. In CarPlay, widgets appear on a dedicated Widgets screen. For both appearances, WidgetKit uses your [`WidgetFamily.systemSmall`](/documentation/widgetkit/widgetfamily/systemsmall) widget and scales it to fit available space. For more information about supporting StandBy and CarPlay, refer to [Adding StandBy and CarPlay support to your widget](/documentation/widgetkit/adding-standby-and-carplay-support-to-your-widget).

### [Indicate that a widget might not fit a specific context](/documentation/WidgetKit/Preparing-widgets-for-additional-contexts-and-appearances#Indicate-that-a-widget-might-not-fit-a-specific-context)

By default, the system suggests widgets in many contexts, and people can choose widgets in the widget gallery to personalize their system experience. However, a widget might not be a good fit for a specific context. For example, a widget that relies on high-resolution photos and background colors for its functionality may not work well on the Lock Screen, where the system applies a vibrant treatment to the widget. To indicate that a widget doesn’t work well in a specific context, use [`disfavoredLocations(_:for:)`](/documentation/SwiftUI/WidgetConfiguration/disfavoredLocations\(_:for:\)) and provide the applicable [`WidgetLocation`](/documentation/widgetkit/widgetlocation). As a result, the widget appears in the widget gallery’s “Other” section for the disfavored location.

### [Verify font sizes in macOS](/documentation/WidgetKit/Preparing-widgets-for-additional-contexts-and-appearances#Verify-font-sizes-in-macOS)

When people place an iPhone widget on a Mac desktop, the system renders it using iOS font metrics. However, a native Mac app’s widgets use macOS font sizing. If you’re sharing code across your iOS and macOS targets in your Xcode project, make sure to verify font sizing in macOS and adjust it for macOS as needed.

## [See Also](/documentation/WidgetKit/Preparing-widgets-for-additional-contexts-and-appearances#see-also)

### [Presentation](/documentation/WidgetKit/Preparing-widgets-for-additional-contexts-and-appearances#Presentation)

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

Creating views for widgets, Live Activities, and watch complications](/documentation/widgetkit/creating-views-for-widgets-live-activities-and-watch-complications)

Implement glanceable views with WidgetKit and SwiftUI.

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