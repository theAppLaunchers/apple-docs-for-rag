Framework

# WidgetKit

Extend the reach of your app by creating widgets, watch complications, Live Activities, and controls.

iOS 14.0+iPadOS 14.0+Mac Catalyst 14.0+macOS 11.0+visionOS 26.0+BetawatchOS 9.0+

## [Overview](/documentation/WidgetKit#Overview)

Using WidgetKit, you can make your app’s content available in contexts outside the app and extend its reach by building an ecosystem of glanceable, up-to-date experiences.

![A conceptual image that shows a small widget on iPhone, a rectangular widget on Apple Watch, and a small widget on the Mac desktop.](https://docs-assets.developer.apple.com/published/273bac77dde0ed1da3f887a44dd0a092/widgetkit-hero%402x.png)

The ecosystem that WidgetKit enables consists of:

**Widgets**

Widgets elevate a small amount of timely, personally relevant information from your app, display it where people can see it at a glance, and offer specific app functionality without launching the app. On iPhone and iPad, people put widgets in Today View, on the Home Screen, and on the Lock Screen. On Mac, people put native Mac app widgets on the desktop and in Notification Center. Additionally, people place iPhone widgets in locations like a Mac desktop and Notification Center, or in CarPlay. On Apple Watch, widgets appear in the Smart Stack, and on Apple Vision Pro, widgets become three-dimensional objects that people pin to horizontal and vertical surfaces.

**Smart Stacks**

On iPhone and iPad, people stack widgets on their Home Screen and create Smart Stacks that use Smart Rotate to show the most contextually relevant widget. On Apple Watch, the system intelligently displays widgets that are most relevant to someone’s personal context. Additionally, a person configures a widget to always appear in the Smart Stack or pins it to a fixed position.

**Watch complications**

People place watch complications on the Apple Watch face to view timely, relevant information when they lift their wrist. Additionally, the Smart Stack on Apple Watch offers space for up to three complications.

**Live Activities**

Live Activities display up-to-date content from your app such as event and task information on the Lock Screen or in the Dynamic Island. Live Activities use [ActivityKit](/documentation/ActivityKit) for updates and optionally the Apple Push Notification service (APNs) to send ActivityKit push notifications. For more information, refer to [ActivityKit](/documentation/ActivityKit).

**Controls**

Controls act as a button or toggle that allows people to perform actions you describe with the [App Intents](/documentation/AppIntents) framework in Control Center, on the Lock Screen, and from the Action button. A button control might initiate an action from your app, or open your app to a specific view, and a toggle might turn a light on and off or open and close a garage door. Controls appear in Control Center or as menu bar items and in Control Center on Apple Watch.

### [Develop glanceable features iteratively](/documentation/WidgetKit#Develop-glanceable-features-iteratively)

WidgetKit enables features across iPad, iPhone, the Mac, Apple Watch, and Apple Vision Pro, but only in a way that best fits a person’s device and personal needs. For example, WidgetKit powers widgets on all platforms in various sizes. It also powers Live Activities and controls, features that aren’t available on Apple Vision Pro.

Even though not every feature that WidgetKit powers is available on every platform or device, widgets, Live Activities, controls, and watch complications share technology and design similarities. This makes it easy to develop features in tandem and to expand usage across contexts.

Use an iterative approach and start with support for one feature or select sizes of widgets — for example, start with a small widget as described in [Creating a widget extension](/documentation/widgetkit/creating-a-widget-extension), but plan and design additional sizes and features across platforms from the beginning. Then allow people to view your content in as many contexts as possible. For more information, refer to [Developing a WidgetKit strategy](/documentation/widgetkit/developing-a-widgetkit-strategy).

### [Understand interactivity and personalization](/documentation/WidgetKit#Understand-interactivity-and-personalization)

The WidgetKit ecosystem enables people to view your app content in new contexts and offers specific interactions with your app when and where they need it:

*   People tap a widget, watch complication, or Live Activity to launch the corresponding app or the app’s scene with matching information or functionality. For example, tapping an Emoji Ranger widget or watch complication launches the scene in the app that matches the displayed hero. For more information, refer to [Linking to specific app scenes from your widget or Live Activity](/documentation/widgetkit/linking-to-specific-app-scenes-from-your-widget-or-live-activity).
    
*   People use buttons and toggles in widgets, controls, and Live Activities to interact with your app without launching it. For example, the large widget of the [Emoji Rangers: Supporting Live Activities, interactivity, and animations](/documentation/widgetkit/emoji-rangers-supporting-live-activities-interactivity-and-animations) sample code project includes a button that people tap to give the healing capability of their hero a temporary boost.
    

In addition to offering relevant information and specific interactivity at a glance, people use widgets, watch complications, Live Activities, and controls to personalize their devices:

*   People configure widgets and watch complications to display details specific to their needs. For example, a widget of the [Emoji Rangers: Supporting Live Activities, interactivity, and animations](/documentation/widgetkit/emoji-rangers-supporting-live-activities-interactivity-and-animations) sample code project allows people to configure the hero that appears on the widget.
    
*   People arrange widgets and watch complications in the way that works best for them. When they stack widgets and enable Smart Rotate on iPhone or iPad, WidgetKit automatically rotates the most relevant widget to the top, making sure people see the most important details at the right time. On Apple Watch, the Smart Stack displays widgets based on contextual relevance, and people pin a favorite widget to a fixed position in the Smart Stack.
    

### [Update content with timelines and push notifications](/documentation/WidgetKit#Update-content-with-timelines-and-push-notifications)

Widgets and watch complications use a special mechanism to update their content: You create a timeline of data updates and hand it to WidgetKit. WidgetKit then makes sure the widget or complication updates its content in an energy-efficient way. For more information on timelines, refer to [Keeping a widget up to date](/documentation/widgetkit/keeping-a-widget-up-to-date). Additionally, widgets can receive updates by using the Apple Push Notification service (APNs) and remote push notifications.

Live Activities don’t use timelines to update their content. Instead, they use [ActivityKit](/documentation/ActivityKit) and ActivityKit push notifications you send with APNs. For more information, refer to [ActivityKit](/documentation/ActivityKit).

Controls don’t use timelines to update their content. Instead, your controls update their content when someone uses them, the app reloads them, or the system receives a remote push notification from APNs.

### [Create a focused, glanceable design](/documentation/WidgetKit#Create-a-focused-glanceable-design)

Widgets, watch complications, Live Activities, and controls are small and require a focused, glanceable design. For design guidance, refer to [Human Interface Guidelines > Widgets](https://developer.apple.com/design/human-interface-guidelines/components/system-experiences/widgets), [Human Interface Guidelines > Complications](https://developer.apple.com/design/human-interface-guidelines/components/system-experiences/complications), [Human Interface Guidelines > Live Activities](https://developer.apple.com/design/human-interface-guidelines/components/system-experiences/live-activities), and [Human Interface Guidelines > Controls](https://developer.apple.com/design/human-interface-guidelines/controls).

## [Topics](/documentation/WidgetKit#topics)

### [Essentials](/documentation/WidgetKit#Essentials)

[

Developing a WidgetKit strategy](/documentation/widgetkit/developing-a-widgetkit-strategy)

Explore features, tasks, related frameworks, and constraints as you make a plan to implement widgets, controls, watch complications, and Live Activities.

[

WidgetKit updates](/documentation/Updates/WidgetKit)

Learn about important changes in WidgetKit.

### [Widget creation](/documentation/WidgetKit#Widget-creation)

[

Creating a widget extension](/documentation/widgetkit/creating-a-widget-extension)

Display your app’s content in a convenient, informative widget on various devices.

[

Supporting additional widget sizes](/documentation/widgetkit/supporting-additional-widget-sizes)

Offer widgets in additional contexts by adding support for various widget sizes.

[

Creating accessory widgets and watch complications](/documentation/widgetkit/creating-accessory-widgets-and-watch-complications)

Support accessory widgets that appear on the Lock Screen and as complications on Apple Watch.

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

### [Presentation](/documentation/WidgetKit#Presentation)

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

### [visionOS widgets](/documentation/WidgetKit#visionOS-widgets)

[

Updating your widgets for visionOS](/documentation/widgetkit/updating-your-widgets-for-visionos)

Choose widget styles specific to visionOS, support recessed and elevated appearances, and add proximity awareness to your widget.

[`@MainActor @preconcurrency func widgetTexture(_ material: WidgetTexture) -> some WidgetConfiguration`](/documentation/SwiftUI/WidgetConfiguration/widgetTexture\(_:\)) 

Specifies the widget texture for this widget.

Beta

```swift
```swift
```swift
struct WidgetTexture
```
```

Values that define the texture of the widget’s coating layer.

Beta
```

[`@MainActor @preconcurrency func supportedMountingStyles(_ styles: [WidgetMountingStyle]) -> some WidgetConfiguration`](/documentation/SwiftUI/WidgetConfiguration/supportedMountingStyles\(_:\)) 

Specifies the mounting style for this widget.

Beta

```swift
```swift
```swift
struct WidgetMountingStyle
```
```

Values that define the widget’s supported mounting style.
```
```swift
```swift
```swift
struct LevelOfDetail
```
```

The level of detail the view is recommended to have.
```

### [Interactivity](/documentation/WidgetKit#Interactivity)

[

Adding interactivity to widgets and Live Activities](/documentation/widgetkit/adding-interactivity-to-widgets-and-live-activities)

Include buttons or toggles in a widget or Live Activity to offer app functionality without launching the app.

[

Animating data updates in widgets and Live Activities](/documentation/widgetkit/animating-data-updates-in-widgets-and-live-activities)

Use SwiftUI animations to indicate data updates in your widgets and Live Activities.

[

Linking to specific app scenes from your widget or Live Activity](/documentation/widgetkit/linking-to-specific-app-scenes-from-your-widget-or-live-activity)

Add deep links to your widgets and Live Activities that enable people to open a specific scene in your app.

### [Configurable widgets](/documentation/WidgetKit#Configurable-widgets)

[

Making a configurable widget](/documentation/widgetkit/making-a-configurable-widget)

Give people the option to customize their widgets by adding a custom app intent to your project.

[

Migrating widgets from SiriKit Intents to App Intents](/documentation/widgetkit/migrating-from-sirikit-intents-to-app-intents)

Configure your widgets for backward compatibility.

```swift
```swift
```swift
struct AppIntentConfiguration
```
```

An object describing the content of a widget that uses a custom intent to provide user-configurable options.
```
```swift
```swift
```swift
struct WidgetInfo
```
```

A structure that contains information about user-configured widgets.
```
```swift
```swift
```swift
struct AppIntentRecommendation
```
```

An object that describes a recommended intent configuration for a user-customizable widget.
```
```swift
```swift
```swift
struct IntentConfiguration
```
```

An object describing the content of a widget that uses a custom intent definition to provide user-configurable options.
```
```swift
```swift
```swift
struct IntentRecommendation
```
```

An object that describes a recommended intent configuration for a user-customizable widget.
```

### [Timeline management](/documentation/WidgetKit#Timeline-management)

[

Keeping a widget up to date](/documentation/widgetkit/keeping-a-widget-up-to-date)

Plan your widget’s timeline to show timely, relevant information using dynamic views, and update the timeline when things change.

```swift
```swift
```swift
protocol TimelineProvider
```
```

A type that advises WidgetKit when to update a widget’s display.
```
```swift
```swift
```swift
protocol AppIntentTimelineProvider
```
```

A type that advises WidgetKit when to update a user-configurable widget’s display.
```
```swift
```swift
```swift
protocol IntentTimelineProvider
```
```

A type that advises WidgetKit when to update a user-configurable widget’s display.
```
```swift
```swift
```swift
struct TimelineProviderContext
```
```

An object that contains details about how a widget is rendered, including its size and whether it appears in the widget gallery.
```
```swift
```swift
```swift
protocol TimelineEntry
```
```

A type that specifies the date to display a widget, and, optionally, indicates the current relevance of the widget’s content.
```
```swift
```swift
```swift
struct Timeline
```
```

An object that specifies a date for WidgetKit to update a widget’s view.
```
```swift
```swift
```swift
class WidgetCenter
```
```

An object that contains a list of user-configured widgets and is used for reloading widget timelines.
```

### [Push notification updates](/documentation/WidgetKit#Push-notification-updates)

[

Updating widgets with WidgetKit push notifications](/documentation/widgetkit/updating-widgets-with-widgetkit-push-notifications)

Use WidgetKit to receive push tokens and reload your widgets with remote push notifications.

```swift
```swift
```swift
protocol WidgetPushHandler
```
```

A type that can receive push information about widget refreshes and relevance refreshes.
```
```swift
```swift
```swift
struct WidgetPushInfo
```
```

A structure that contains information about the push token for updating widgets and widget relevances.
```

### [watchOS widgets](/documentation/WidgetKit#watchOS-widgets)

```swift
```swift
```swift
```swift
struct AccessoryWidgetGroup
```
```

A view type that has a label at the top and three content views masked with a circle or rounded square.
```
```swift
```swift
```swift
struct AccessoryWidgetGroupStyle
```
```

The style for an [`AccessoryWidgetGroup`](/documentation/widgetkit/accessorywidgetgroup) view.
```

[

Migrating ClockKit complications to WidgetKit](/documentation/widgetkit/converting-a-clockkit-app)

Leverage WidgetKit’s API to create watchOS complications using SwiftUI.
```

### [Accessibility](/documentation/WidgetKit#Accessibility)

[

Adding accessible descriptions to widgets and Live Activities](/documentation/ActivityKit/adding-accessible-descriptions-to-widgets-and-live-activities)

Describe the interface elements of your widgets and Live Activities to help people understand what they represent.

### [Location services in widgets](/documentation/WidgetKit#Location-services-in-widgets)

[

Accessing location information in widgets](/documentation/widgetkit/accessing-location-information-in-widgets)

Incorporate location information into your widget presentation to make it more relevant and contextual.

### [Networking](/documentation/WidgetKit#Networking)

[

Making network requests in a widget extension](/documentation/widgetkit/making-network-requests-in-a-widget-extension)

Update your widget with new information you fetch with a network request.

### [Smart Stacks](/documentation/WidgetKit#Smart-Stacks)

[

Increasing the visibility of widgets in Smart Stacks](/documentation/widgetkit/widget-suggestions-in-smart-stacks)

Provide contextual information and donate intents to the system to make sure your widget appears prominently in Smart Stacks.

```swift
```swift
```swift
struct TimelineEntryRelevance
```
```

An object that describes the relative importance of a timeline entry compared to other entries in the current and past timelines.
```
```swift
```swift
```swift
struct RelevanceConfiguration
```
```

A type that describes the content of a widget that uses relevance clues.

Beta
```
```swift
```swift
```swift
protocol RelevanceEntriesProvider
```
```

A type that provides the content for a widget that uses relevance clues to display information in the Smart Stack.

Beta
```
```swift
```swift
```swift
protocol RelevanceEntry
```
```

A type that specifies the information to render a widget at a specific relevance configuration.

Beta
```
```swift
```swift
```swift
struct WidgetRelevance
```
```

A type collecting the relevances for a widget kind.
```
```swift
```swift
```swift
struct WidgetRelevanceAttribute
```
```

A type describing when a specific widget could be relevant.
```
```swift
```swift
```swift
struct WidgetRelevanceGroup
```
```

A type for configuring widget behavior in the watchOS Smart Stack.
```

### [Widget preview and debugging](/documentation/WidgetKit#Widget-preview-and-debugging)

[

Previewing widgets and Live Activities in Xcode](/documentation/widgetkit/previewing-widgets-and-live-activities-in-xcode)

Use Xcode previews to iteratively develop, fine-tune, and troubleshoot widgets and Live Activities.

[

Debugging widgets](/documentation/widgetkit/debugging-widgets)

Set environment variables in Xcode to control your widget’s configuration in the debugger.

```swift
```swift
```swift
struct WidgetPreviewContext
```
```

A specification for the context of a widget preview.
```

[

API Reference

Preview macros](/documentation/widgetkit/preview-macros)

Use Swift macros to create widget previews in Xcode.

### [Live Activities](/documentation/WidgetKit#Live-Activities)

```swift
```swift
```swift
```swift
struct ActivityConfiguration
```
```

An object that describes the content of a Live Activity.
```
```swift
```swift
```swift
struct DynamicIsland
```
```

The layout and configuration for a Live Activity that appears in the Dynamic Island.
```
```swift
```swift
```swift
let NSUserActivityTypeLiveActivity: String
```
```

A string that the system passes to the app on launch from a Live Activity that doesn’t provide a URL.
```
```swift
```swift
```swift
enum ActivityPreviewViewKind
```
```

Values that represent Live Activity presentations for use in Xcode previews.
```
```swift
```swift
```swift
enum ActivityFamily
```
```

A family that defines the Live Activity’s size.
```
```

### [Controls](/documentation/WidgetKit#Controls)

[

Creating controls to perform actions across the system](/documentation/widgetkit/creating-controls-to-perform-actions-across-the-system)

Perform your app’s actions from Control Center, the Lock Screen, and the Action button.

[

Adding refinements and configuration to controls](/documentation/widgetkit/adding-refinements-and-configuration-to-controls)

Customize the way controls display across the system and offer people the ability to configure them.

```swift
```swift
```swift
struct ControlWidgetToggle
```
```

A control template representing a toggle.
```
```swift
```swift
```swift
class ControlCenter
```
```

An object that contains a list of user-configured controls and is used for reloading controls.
```
```swift
```swift
```swift
struct ControlWidgetButton
```
```

A control template representing a button.
```

### [Control values and previews](/documentation/WidgetKit#Control-values-and-previews)

```swift
```swift
```swift
```swift
protocol ControlValueProvider
```
```

A type that provides a value to a control widget template.
```
```swift
```swift
```swift
protocol AppIntentControlValueProvider
```
```

A type that uses a custom intent to provide a value to a control template.
```
```

### [Control configuration](/documentation/WidgetKit#Control-configuration)

```swift
```swift
```swift
```swift
struct StaticControlConfiguration
```
```

The description of a control widget that has no user-configurable options.
```
```swift
```swift
```swift
struct AppIntentControlConfiguration
```
```

The description of a control widget that uses a custom intent to provide user-configurable options.
```
```swift
```swift
```swift
struct ControlInfo
```
```

A structure that contains information about user-configured controls.
```
```

### [Control updates](/documentation/WidgetKit#Control-updates)

[

Updating controls locally and remotely](/documentation/widgetkit/updating-controls-locally-and-remotely)

Update and reload controls from your app or using push notifications.

```swift
```swift
```swift
protocol ControlPushHandler
```
```

A type that can receive push information about user-configured controls.
```
```swift
```swift
```swift
struct ControlPushInfo
```
```

A structure that contains information about the push token of a user-configured control.
```

Beta Software

This documentation contains preliminary information about an API or technology in development. This information is subject to change, and software implemented according to this documentation should be tested with final operating system software.

[Learn more about using Apple's beta software](https://developer.apple.com/support/beta-software/)