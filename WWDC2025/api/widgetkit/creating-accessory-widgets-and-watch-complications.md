*   [WidgetKit](/documentation/widgetkit)
*   Creating accessory widgets and watch complications

Article

# Creating accessory widgets and watch complications

Support accessory widgets that appear on the Lock Screen and as complications on Apple Watch.

## [Overview](/documentation/WidgetKit/Creating-accessory-widgets-and-watch-complications#Overview)

WidgetKit allows you to extend the reach of your app to the Lock Screen on iPhone and iPad, and to the Smart Stack on Apple Watch as _accessory widgets_. Accessory widgets also appear as watch complications on Apple Watch. They display your app’s most relevant, glanceable content in highly visible contexts and let people quickly access your app for more details.

Widgets and watch complications use WidgetKit and SwiftUI views, enabling you to:

*   Update your existing widgets’ code to support accessory widgets.
    
*   Offer WidgetKit complications for your watchOS app, replace ClockKit complications, and share more code between your iOS and watchOS apps.
    
*   Create watch complications and Lock Screen widgets simultaneously.
    
*   Add support for iOS or watchOS to your app — in addition to platforms you already support — and offer widgets or complications.
    

Your path to creating accessory widgets and WidgetKit complications depends on your project. Before you start coding, make sure to review options available to you and carefully plan your software development project. If you’re new to WidgetKit development, see [Developing a WidgetKit strategy](/documentation/widgetkit/developing-a-widgetkit-strategy).

Related sessions from WWDC22

[Session 10050: Complications and widgets: Reloaded](https://developer.apple.com/videos/play/wwdc2022/10050) and [Session 10051: Go further with complications in WidgetKit](https://developer.apple.com/videos/play/wwdc2022/10051)

Related sessions from WWDC23

[Session 10309:Design widgets for the Smart Stack on Apple Watch](https://developer.apple.com/videos/play/wwdc2023/10309) and [Session 10027: Bring widgets to new places](https://developer.apple.com/videos/play/wwdc2023/10027)

### [Create a new app that offers widgets and watch complications](/documentation/WidgetKit/Creating-accessory-widgets-and-watch-complications#Create-a-new-app-that-offers-widgets-and-watch-complications)

If you create a new app, support iOS and watchOS and offer widgets and complications right from the start. This allows you to create a shared code base and reduces the need for costly code changes later in the app development process.

To get started:

1.  Open Xcode and create a new project.
    
2.  Choose the watchOS app template and select Watch App with New Companion iOS App in the “Choose options for your new project” sheet.
    
3.  Add a new watchOS widget extension target to your project.
    
4.  Add a new iOS widget extension target to your project.
    
5.  Add code for your iOS and watchOS apps, and create iOS widgets — including for the Lock Screen — and watchOS complications simultaneously using SwiftUI views and WidgetKit.
    

To learn more about creating widgets and building apps with SwiftUI, see [Creating a widget extension](/documentation/widgetkit/creating-a-widget-extension) and [SwiftUI](/documentation/SwiftUI). For more information on creating watchOS apps, see [watchOS apps](/documentation/watchOS-Apps).

### [Add accessory widgets to your existing iOS App](/documentation/WidgetKit/Creating-accessory-widgets-and-watch-complications#Add-accessory-widgets-to-your-existing-iOS-App)

If your app supports widgets, adding accessory widgets works like supporting any other widget size. To learn more, see [Supporting additional widget sizes](/documentation/widgetkit/supporting-additional-widget-sizes).

If you don’t offer widgets in your app, add a widget extension to your app and support accessory widgets from the start. To learn more about adding a widget extension to your project, see [Creating a widget extension](/documentation/widgetkit/creating-a-widget-extension).

Additionally, consider adding support for watchOS with WidgetKit complications by adding a watchOS app target and a watchOS widget extension target. To learn more about creating a watchOS app, see [watchOS apps](/documentation/watchOS-Apps).

### [Add WidgetKit complications to your existing watchOS app](/documentation/WidgetKit/Creating-accessory-widgets-and-watch-complications#Add-WidgetKit-complications-to-your-existing-watchOS-app)

If your existing watchOS app doesn’t offer complications, add a watchOS widget extension to your project in Xcode, and create complications with WidgetKit. Implementing WidgetKit complications works like creating widgets. For more information about creating a widget extension, see [Creating a widget extension](/documentation/widgetkit/creating-a-widget-extension).

If your watchOS app offers ClockKit complications, continue to use these to support watchOS 8 and earlier. However, plan to migrate your existing ClockKit complications to WidgetKit as described in [Migrating ClockKit complications to WidgetKit](/documentation/widgetkit/converting-a-clockkit-app).

Important

As soon as you offer a widget-based complication, the system stops calling ClockKit APIs. For example, it no longer calls your [`CLKComplicationDataSource`](/documentation/ClockKit/CLKComplicationDataSource) object’s methods to request timeline entries. The system may still wake your data source for migration requests.

Additionally, consider adding support for iOS by adding an iOS app target to your Xcode project if your watchOS app doesn’t come with an iOS companion app.

## [See Also](/documentation/WidgetKit/Creating-accessory-widgets-and-watch-complications#see-also)

### [Widget creation](/documentation/WidgetKit/Creating-accessory-widgets-and-watch-complications#Widget-creation)

[

Creating a widget extension](/documentation/widgetkit/creating-a-widget-extension)

Display your app’s content in a convenient, informative widget on various devices.

[

Supporting additional widget sizes](/documentation/widgetkit/supporting-additional-widget-sizes)

Offer widgets in additional contexts by adding support for various widget sizes.

[

Emoji Rangers: Supporting Live Activities, interactivity, and animations](/documentation/widgetkit/emoji-rangers-supporting-live-activities-interactivity-and-animations)

Offer Live Activities, controls, animate data updates, and add interactivity to widgets.

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