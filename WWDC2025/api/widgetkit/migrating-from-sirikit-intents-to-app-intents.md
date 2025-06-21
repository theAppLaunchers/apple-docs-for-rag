*   [WidgetKit](/documentation/widgetkit)
*   Migrating widgets from SiriKit Intents to App Intents

Article

# Migrating widgets from SiriKit Intents to App Intents

Configure your widgets for backward compatibility.

## [Overview](/documentation/WidgetKit/Migrating-from-SiriKit-Intents-to-App-Intents#Overview)

Starting with iOS 17 and macOS 14, you use App Intents to create configurable widgets. If you have an existing configurable widgets that uses SiriKit Intents, you can add App Intents while continuing to support older operating system versions.

If the minimum version your app supports is iOS 17, macOS 14, or watchOS 10, use App Intents for your widget configurations. See [Making a configurable widget](/documentation/widgetkit/making-a-configurable-widget) for details.

For additional information about converting custom intents to App Intents, watch the Tech Talks session video [Migrate custom intents to App Intents](https://developer.apple.com/videos/play/tech-talks/10168).

### [Convert SiriKit Intents to App Intents](/documentation/WidgetKit/Migrating-from-SiriKit-Intents-to-App-Intents#Convert-SiriKit-Intents-to-App-Intents)

Xcode provides automatic conversion from SiriKit Intents to App Intents. Follow these steps to convert an existing intent to an app intent:

1.  In the Project Navigator, select the Intent Definition File that contains the intent you wish to convert.
    
2.  Choose the Editor > Convert to App Intent… menu item.
    
3.  Select one or more intent definition files from the list of intent definition files, and click Next.
    
4.  Select one or more intents from the list of available intents, and click Next.
    
5.  Select a location to save the new files in your project, and the targets in which to include the converted intents.
    

Xcode generates source files for new types that conform to the [`CustomIntentMigratedAppIntent`](/documentation/AppIntents/CustomIntentMigratedAppIntent) protocol, and sets the `intentClassName` property to the name of the SiriKit Intent.

### [Update the widget configuration](/documentation/WidgetKit/Migrating-from-SiriKit-Intents-to-App-Intents#Update-the-widget-configuration)

In the widget’s `body` method, add code that does the following:

*   Instead of using an `IntentConfiguration`, create an [`AppIntentConfiguration`](/documentation/widgetkit/appintentconfiguration).
    
*   Instead of passing an `INIntent` type to the app configuration’s initializer, pass the newly converted intent type created as described in the steps above. This new intent type conforms to [`WidgetConfigurationIntent`](/documentation/AppIntents/WidgetConfigurationIntent) .
    
*   Instead of passing an `IntentTimelineProvider`, pass a type that conforms to [`AppIntentTimelineProvider`](/documentation/widgetkit/appintenttimelineprovider).
    

To continue supporting versions earlier than iOS 17, macOS 14, and watchOS 10, factor the creation of the widget’s configuration to a type-erased method that the `body` method calls, as shown below.

```swift
```swift
```swift
```swift
```swift
```swift
struct MyWidget: Widget {
```
```
    // Helper method to create the appropriate configuration depending
    // on the operating system version.
    func makeWidgetConfiguration() -> some WidgetConfiguration {
        if #available(iOS 17.0, macOS 14.0, watchOS 10.0, *) {
            return AppIntentConfiguration(kind: kind, intent: MyAppIntent.self, provider: MyAppIntentProvider()) { entry in
                MyAppIntentWidgetEntryView(entry: entry)
            }
        } else {
            return IntentConfiguration(kind: kind, intent: MyIntent.self, provider: MyIntentProvider()) { entry in
                MyIntentWidgetEntryView(entry: entry)
            }
        }
    }
    var body: some WidgetConfiguration {
        makeWidgetConfiguration()
            .configurationDisplayName("My Widget")
            .description("This is an example widget.")
    }
}
```
```
```
```

After you create app intent types, and switch to using `AppIntentConfiguration`, the system migrates the user’s widgets configured with SiriKit Intents. The system:

*   Identifies the name of the custom `INIntent` in the widget’s stored configuration.
    
*   Identifies the new app intent that conforms to `CustomIntentMigratedAppIntent`, in which the `intentClassName` matches the name of the custom `INIntent`.
    
*   Maps the parameters from the `INIntent` configuration to the `CustomIntentMigratedAppIntent`, matching the parameter name and type.
    
*   Creates an instance of the new app intent with the mapped parameters.
    
*   Uses the new app intent for the widget’s configuration instead of the `INIntent`.
    

Important

If the name or type of the parameters don’t match, the system omits the parameter from the app intent, and the user’s configuration is lost. For example, if the `INIntent` parameter is an `INPerson`, use `IntentPerson` for the app intent type. If the parameter’s type is an enum or custom object, the new type must conform to `AppEnum` or `TransientAppEntity`, respectively.

### [Implement an app intent timeline provider](/documentation/WidgetKit/Migrating-from-SiriKit-Intents-to-App-Intents#Implement-an-app-intent-timeline-provider)

To generate timeline entries that use app intents, create a timeline provider that conforms to [`AppIntentTimelineProvider`](/documentation/widgetkit/appintenttimelineprovider). The functionality of an `AppIntentTimelineProvider` is the same as an `IntentTimelineProvider`; the difference is the associated `Intent` type. For an `AppIntentTimelineProvider`, the `Intent` type is `WidgetConfigurationIntent`; for an `IntentTimelineProvider`, it’s an `INIntent`.

Tip

If your app supports older operating system versions, minimize code duplication by factoring common code out into a separate type used by both providers.

When designing the timeline entries that the timeline providers generate, consider these two approaches:

1.  Use separate timeline entry types for each provider: one that includes the app intent, and another that includes a SiriKit intent.
    
2.  Use a single timeline entry type that includes both an app intent and a SiriKit intent.
    

The first approach involves maintaining separate types, possibly duplicating properties in both types, but it’s simpler conceptually. The second approach reduces any duplication, but requires optional types for the intent properties.

### [Display content based on an app intent](/documentation/WidgetKit/Migrating-from-SiriKit-Intents-to-App-Intents#Display-content-based-on-an-app-intent)

WidgetKit displays a widget’s content by calling the widget configuration’s `content` closure. If you have separate types for your timeline entries, you need to provide a separate content closure for each type.

If you share the same timeline entry type across both intent provider types, you can use a single content closure with logic conditional to the intent in the entry.

## [See Also](/documentation/WidgetKit/Migrating-from-SiriKit-Intents-to-App-Intents#see-also)

### [Configurable widgets](/documentation/WidgetKit/Migrating-from-SiriKit-Intents-to-App-Intents#Configurable-widgets)

[

Making a configurable widget](/documentation/widgetkit/making-a-configurable-widget)

Give people the option to customize their widgets by adding a custom app intent to your project.

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