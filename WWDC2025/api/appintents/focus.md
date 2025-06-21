Collection

*   [App Intents](/documentation/appintents)
*   Focus

API Collection

# Focus

Adjust your app’s behavior and filter incoming notifications when the current Focus changes.

## [Overview](/documentation/AppIntents/focus#Overview)

![](https://docs-assets.developer.apple.com/published/5df0da09dac6ff6a8d59c38d2909275b/focus-filters-hero%402x.png)

People use Focus on macOS, iOS, and iPadOS to minimize distractions. For example, someone might use a Work Focus to hide notifications from personal email or message accounts. When someone engages a Focus, the system executes your app’s custom [`SetFocusFilterIntent`](/documentation/appintents/setfocusfilterintent). Define a version of this intent to update your app’s configuration and filter incoming notifications.

Related sessions from WWDC22

Session 10121: [Meet Focus filters](https://developer.apple.com/videos/play/wwdc2022/10121).

## [Topics](/documentation/AppIntents/focus#topics)

### [Focus filters](/documentation/AppIntents/focus#Focus-filters)

```swift
```swift
```swift
```swift
protocol SetFocusFilterIntent
```
```

An interface for providing an app intent that you use to adapt your app’s behavior when Focus changes.
```

[

Defining your app’s Focus filter](/documentation/appintents/focus/defining_your_app_s_focus_filter)

Customize your app’s behavior to reflect the device’s current Focus.

```swift
```swift
```swift
struct FocusFilterAppContext
```
```

A type that contains app-specific contextual information for a particular Focus, such as the notification filter criteria to apply.
```
```swift
```swift
```swift
struct FocusFilterSuggestionContext
```
```

A type you use to suggest app configurations for a given Focus.
```
```

### [Errors](/documentation/AppIntents/focus#Errors)

```swift
```swift
```swift
```swift
enum SetFocusFilterIntentError
```
```

Errors that can occur when you try to retrieve the current Focus configuration settings.
```
```

## [See Also](/documentation/AppIntents/focus#see-also)

### [Other system experiences](/documentation/AppIntents/focus#Other-system-experiences)

[

Making app entities available in Spotlight](/documentation/appintents/making-app-entities-available-in-spotlight)

Allow people to find your app’s content in Spotlight by donating app entities to its semantic index.

[

API Reference

Action button on iPhone and Apple Watch](/documentation/appintents/actionbutton)

Enable people to run your App Shortcuts with the Action button on iPhone or to start your app’s workout or dive sessions using the Action button on Apple Watch.

[

Developing a WidgetKit strategy](/documentation/WidgetKit/Developing-a-WidgetKit-strategy)

Explore features, tasks, related frameworks, and constraints as you make a plan to implement widgets, controls, watch complications, and Live Activities.