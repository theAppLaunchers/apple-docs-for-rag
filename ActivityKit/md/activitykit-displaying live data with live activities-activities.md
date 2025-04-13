

- ActivityKit
-  Displaying live data with Live Activities 

Article

# Displaying live data with Live Activities

Display your app’s data in the Dynamic Island and on the Lock Screen and offer quick interactions.

## Overview

Live Activities display your app’s most current data on the iPhone or iPad Lock Screen and in the Dynamic Island, allowing people to refer to live information at a glance and perform quick actions that are related to the displayed information.

To offer Live Activities, add code to your existing widget extension or create a new widget extension if your app doesn’t already include one. Live Activities use WidgetKit functionality and SwiftUI for their user interface. ActivityKit’s role is to handle the life cycle of each Live Activity: You use its API to request, update, and end a Live Activity and to receive ActivityKit push notifications.

For design guidance, refer to Human Interface Guidelines > Live Activities.

Related sessions from WWDC23

Session 10184: Meet ActivityKit and Session 10194: Design dynamic Live Activities

### Review Live Activity presentations

Live Activities come in different presentations for the Lock Screen and the Dynamic Island. The Lock Screen presentation appears on all devices. On an unlocked device that doesn’t support the Dynamic Island, the Lock Screen presentation also appears as a banner for Live Activity updates that include an alert configuration. For example, if a person uses Mail on a device that doesn’t support the Dynamic Island while the Live Activity receives an update with an alert configuration, the system displays the Lock Screen presentation as a banner at the top of the screen to let them know about the updated Live Activity.

Devices that support the Dynamic Island display Live Activities in the Dynamic Island using several presentations. When there’s only one ongoing Live Activity, the system uses the compact presentation. It’s composed of two elements: one that displays on the leading side of the TrueDepth camera, and one that displays on the trailing side. Although the leading and trailing presentations are separate views, they form a cohesive view in the Dynamic Island, representing a single piece of information from your app. People can tap a compact Live Activity to open the app and get more details about the event or task. 

When multiple Live Activities from several apps are active, the system uses the circular minimal presentation to display two of them in the Dynamic Island. The system chooses a Live Activity from one app to appear attached to the Dynamic Island while it presents a Live Activity from another app detached from the Dynamic Island. As with a compact Live Activity, people can tap a minimal Live Activity to open the app and get more details about the event or task.

When people touch and hold a Live Activity in a compact or minimal presentation, the system displays the content in an expanded presentation.

The minimal presentation also appears at the top of the iPhone Lock Screen when the device is in StandBy — in landscape orientation, charging, and with the display positioned at an angle to face the room. If a person taps the minimal presentation in StandBy, the Live Activity expands to fill the whole display using the Lock Screen presentation.

To add support for Live Activities in your app, you must support all presentations.

### Understand constraints

A Live Activity can be active for up to eight hours unless its app or a person ends it before this limit. After the eight-hour limit, the system automatically ends the Live Activity, and immediately removes it from the Dynamic Island. However, the Live Activity remains on the Lock Screen until a person removes it or for up to four additional hours before the system removes it — whichever comes first. As a result, a Live Activity remains on the Lock Screen for a maximum of 12 hours.

For more information about ending a Live Activity, refer to the “End the Live Activity” section below.

The system requires image assets for a Live Activity to use a resolution that’s smaller or equal to the size of the presentation for a device. If you use an image asset that’s larger than the size of the Live Activity presentation, the system might fail to start the Live Activity. For example, an image you use for the minimal presentation of your Live Activity shouldn’t exceed 45x36.67 points. For size guidance of Live Activity presentations, refer to Human Interface Guidelines > Live Activities.

Each Live Activity runs in its own sandbox, and — unlike a widget — it can’t access the network or receive location updates. To update the dynamic data of an active Live Activity, use ActivityKit in your app or allow your Live Activities to receive ActivityKit push notifications as described in Starting and updating Live Activities with ActivityKit push notifications.

Important

Static and dynamic data for a Live Activity, including data for ActivityKit updates and ActivityKit push notifications, can’t exceed a combined size of 4 KB.

### Add support for Live Activities to your app

The code that describes the user interface of your Live Activity is part of your app’s widget extension. If you already offer widgets in your app, add code for the Live Activity to your existing widget extension and reuse code between your widgets and Live Activities. However, although Live Activities leverage WidgetKit’s functionality, they aren’t widgets. In contrast to the timeline mechanism you use to update your widgets’ user interface, you start and update a Live Activity from your app with ActivityKit or with ActivityKit push notifications.

Note

You can create a widget extension to adopt Live Activities without offering widgets. However, consider offering both widgets and Live Activities to allow people to add glanceable information and a personal touch to their device.

To support Live Activities:

1.  Create a widget extension if you haven’t added one to your app and make sure to select “Include Live Activity” when you add a widget extension target to your Xcode project. For more information on creating a widget extension, refer to WidgetKit and Creating a widget extension.

2.  If your project includes an `Info.plist` file, add the Supports Live Activities entry to it, and set its Boolean value to `YES`. Alternatively, open the `Info.plist` file as source code, add the NSSupportsLiveActivities key, then set the type to `Boolean` and its value to `YES`. If your project doesn’t have an `Info.plist` file, add the Supports Live Activities entry to the list of custom iOS target properties for your iOS app target and set its value to `YES`.

3.  Add code that defines an ActivityAttributes structure to describe the static and dynamic data of your Live Activity.

4.  Use the `ActivityAttributes` you defined to create the ActivityConfiguration.

5.  Add code to configure, start, update, and end your Live Activities.

6.  Make your Live Activity interactive with Button or Toggle as described in Adding interactivity to widgets and Live Activities.

7.  Add animations to bring attention to content updates as described in Animating data updates in widgets and Live Activities.

### Define a set of static and dynamic data

After you add a widget extension target that includes Live Activities to your Xcode project, describe the data that your Live Activity displays by implementing ActivityAttributes. The ActivityAttributes inform the system about static data that appears in the Live Activity. You also use ActivityAttributes to declare the required custom Activity.ContentState type that describes the dynamic data of your Live Activity. In the example below from the Apple Developer Documentation sample code project, `AdventureAttributes ` describes the hero information as static data using `let hero: EmojiRanger`. Note how the code defines the Activity.ContentState to encapsulate dynamic data: the current health level of the hero and a string that describes what happens to the hero.

```
import ActivityKit

struct AdventureAttributes: ActivityAttributes {
    struct ContentState: Codable & Hashable {
        let currentHealthLevel: Double
        let eventDescription: String
    }

    let hero: EmojiRanger
}
```

Tip

To make your code more descriptive and easy to read, you can define a type alias for the `ContentState`; for example: `public typealias HeroStatus = ContentState`.

### Add Live Activities to the widget extension

Live Activities leverage WidgetKit. After you add code to describe the data that appears in the Live Activity with the ActivityAttributes structure, add code to return an ActivityConfiguration in your widget implementation.

The following example uses the `AdventureAttributes` structure from the previous example:

```
import WidgetKit
import SwiftUI

struct AdventureActivityConfiguration: Widget {
    var body: some WidgetConfiguration {
        ActivityConfiguration(for: AdventureAttributes.self) { context in
            // Create the presentation that appears on the Lock Screen and as a
            // banner on the Home Screen of devices that don't support the
            // Dynamic Island.
            // ...
        } dynamicIsland: { context in
            // Create the presentations that appear in the Dynamic Island.
            // ...
        }
    }
}
```

Tip

If you select “Include Live Activities” when you add a new widget extension target to your project, Xcode automatically creates a widget bundle for you that includes a widget and a Live Activity.

If your app already offers widgets, add the Live Activity to your WidgetBundle. If you don’t have a WidgetBundle — for example, if you only offer one widget — create a widget bundle as described in Creating a widget extension and then add the Live Activity to it.

### Create the Lock Screen presentation

To create the user interface of the Live Activity, you use SwiftUI in the widget extension you created earlier. Similar to widgets, you don’t provide the size of the user interface for your Live Activity but let the system determine the appropriate dimensions.

Start with the presentation that appears on the Lock Screen. The following code displays the information that the `AdventureAttributes` struct describes using the custom `AdventureLiveActivityView`:

```
struct AdventureActivityConfiguration: Widget {
    var body: some WidgetConfiguration {
        ActivityConfiguration(for: AdventureAttributes.self) { context in
            // Create the presentation that appears on the Lock Screen and as a
            // banner on the Home Screen of devices that don't support the
            // Dynamic Island.
            AdventureLiveActivityView(
                hero: context.attributes.hero,
                isStale: context.isStale,
                contentState: context.state
            )
            .activityBackgroundTint(Color.liveActivityBackground.opacity(0.25))
        } dynamicIsland: { context in
            // Create the presentations that appear in the Dynamic Island.
            // ...
        }
    }
}
```

Note

The system may truncate a Live Activity if its height exceeds 160 points.

On a device that doesn’t support the Dynamic Island, the system displays the Lock Screen presentation as a banner for a Live Activity update if:

- The device is unlocked and its app isn’t in use

- You pass an AlertConfiguration to the update(_:alertConfiguration:) function

On iPhone in StandBy, the Lock Screen presentation appears scaled to fill the screen of the device. Make sure your assets offer a high-enough resolution for StandBy. Additionally, consider updating the Lock Screen presentation to make use of the additional space. To detect Standby, use the isActivityFullscreen environment variable.

### Create the compact and minimal presentations

Live Activities appear in the Dynamic Island of devices that support it. When you start one or more Live Activities and no other app starts a Live Activity, the compact leading and trailing presentations appear together to form a cohesive presentation in the Dynamic Island for one Live Activity.

When more than one app starts a Live Activity, the system chooses which Live Activities are visible and displays two Live Activities using the minimal presentation for each: One minimal presentation appears attached to the Dynamic Island, while the other appears detached. Additionally, the detached minimal presentation appears on the Lock Screen on iPhone in StandBy. If your app starts more than one Live Activity at the same time, you can tell the system which one it should display by setting a relevance score. For more information, refer to the “Configure the Live Activity” section below.

The following example shows how the Emoji Rangers: Supporting Live Activities, interactivity, and animations app provides the required compact and minimal presentations. For the leading presentation, it reuses the custom SwiftUI view `Avatar`. For the trailing presentation, it uses a ProgressView.

```
import SwiftUI
import WidgetKit

struct AdventureActivityConfiguration: Widget {
    var body: some WidgetConfiguration {
        ActivityConfiguration(for: AdventureAttributes.self) { context in
            // Create the presentation that appears on the Lock Screen and as a
            // banner on the Home Screen of devices that don't support the
            // Dynamic Island.
            // ...
        } dynamicIsland: { context in
            // Create the presentations that appear in the Dynamic Island.
            DynamicIsland {
                // Create the expanded presentation.
                // ...
            } compactLeading: {
                // Create the compact leading presentation.
                Avatar(hero: context.attributes.hero, includeBackground: true)
                    .accessibilityLabel("The avatar of \(context.attributes.hero.name).")
            } compactTrailing: {
                // Create the compact trailing presentation.
                ProgressView(value: context.state.currentHealthLevel, total: 1) {
                    let healthLevel = Int(context.state.currentHealthLevel * 100)
                    Text("\(healthLevel)")
                        .accessibilityLabel("Health level at \(healthLevel) percent.")
                }
                .progressViewStyle(.circular)
                .tint(context.state.currentHealthLevel 

### Create the expanded presentation

In addition to the compact and minimal presentations, you must support the expanded presentation. It appears when a person touches and holds a compact or minimal presentation, and it also appears briefly for Live Activity updates.

Use the DynamicIslandExpandedRegionPosition to specify detailed instructions where you want SwiftUI to position your content. The following example shows how the Emoji Rangers: Supporting Live Activities, interactivity, and animations app creates its expanded presentation using a DynamicIslandExpandedContentBuilder:

```
struct AdventureActivityConfiguration: Widget {
    var body: some WidgetConfiguration {
        ActivityConfiguration(for: AdventureAttributes.self) { context in
            // Create the presentation that appears on the Lock Screen and as a
            // banner on the Home Screen of devices that don't support the
            // Dynamic Island.
            // ...
        } dynamicIsland: { context in
            // Create the presentations that appear in the Dynamic Island.
            DynamicIsland {
                // Create the expanded presentation.
                expandedContent(
                    hero: context.attributes.hero,
                    contentState: context.state,
                    isStale: context.isStale
                )
            } compactLeading: {
                // Create the compact leading presentation.
                // ...
            } compactTrailing: {
                // Create the compact trailing presentation.
                // ...
            } minimal: {
                // Create the minimal presentation.
                // ...
            }
        }
    }

    @DynamicIslandExpandedContentBuilder
    private func expandedContent(hero: EmojiRanger,
                                 contentState: AdventureAttributes.ContentState,
                                 isStale: Bool) -> DynamicIslandExpandedContent {
        DynamicIslandExpandedRegion(.leading) {
            LiveActivityAvatarView(hero: hero)
        }

        DynamicIslandExpandedRegion(.trailing) {
            StatsView(
                hero: hero,
                isStale: isStale
            )
        }

        DynamicIslandExpandedRegion(.bottom) {
            HealthBar(currentHealthLevel: contentState.currentHealthLevel)

            EventDescriptionView(
                hero: hero,
                contentState: contentState
            )
        }
    }
}
```

To render views that appear in the expanded Live Activity, the system divides the expanded presentation into different areas. Note how the example returns a DynamicIsland that specifies several DynamicIslandExpandedRegion objects. Pass the following DynamicIslandExpandedRegionPosition values to lay out your content at a specified position in the expanded presentation:

- center places content below the TrueDepth camera.

- leading places content along the leading edge of the expanded Live Activity next to the TrueDepth camera and wraps additional content below it.

- trailing places content along the trailing edge of the expanded Live Activity next to the TrueDepth camera and wraps additional content below it.

- bottom places content below the leading, trailing, and center content.

To render content that appears in the expanded Live Activity, the system first determines the width of the center content while taking into account the minimal width of the leading and trailing content. The system then places and sizes the leading and trailing content based on its vertical position. By default, leading and trailing positions receive an equal amount of horizontal space.

You can tell the system to prioritize one of the `DynamicIslandExpandedRegion` views by passing a `priority` to the init(_:priority:content:) initializer. The system renders the view with the highest priority with the full width of the Dynamic Island. The following illustration shows leading and trailing positions in an expanded presentation with higher priority to render them below the TrueDepth camera.

Note

If content is too wide to appear in a leading position next to the TrueDepth camera, use the belowIfTooWide modifier to render leading content below the TrueDepth camera.

### Customize Live Activities in the Smart Stack on watchOS

Starting with iOS 18 and watchOS 11, Live Activities appear in the Smart Stack on Apple Watch automatically. Updates to your Live Activity on iOS are also automatically sent to Apple Watch. Review your current views to ensure that you’re displaying dynamically updated information that keeps people informed about the state of the activity.

- On iOS, alerting updates animate to display your Dynamic Island Expanded Views. When someone’s Apple Watch receives a Live Activity update, the system automatically launches the Smart Stack, displays your alert, and then shows your Live Activity.

- If your app is in the foreground, a banner displays at the bottom of the Apple Watch screen with your Dynamic Island compact view.

- Tapping a Live Activity on Apple Watch shows a full-screen presentation with an option to open the app on iPhone. If your app has a watch app version, you can opt to open your app on watch with a tap on the Live Activity in the Smart Stack.

Provide a custom Live Activity view for Apple Watch using supplementalActivityFamilies(_:) with a `.small` view modifier. Customize your content view for the Smart Stack using the activityFamily environment value. For watchOS, use `small` to provide an appropriate view for the Smart Stack. For the iOS Lock Screen, use `medium`.

The code below uses `supplementalactivityfamilies(_:)` to specify the size of the Live Activity for devices that use iOS and watchOS.

```
// A RideSharingActivity that supports the watchOS Smart Stack and the iOS Lock Screen.
struct RideSharingActivity: Widget {
    var body: some WidgetConfiguration {
        ActivityConfiguration(for: RideAttributes.self) { context in
            RideSharingView(context: context)
        } dynamicIsland: { context in
            DynamicIsland {
                DynamicIslandExpandedRegion(.bottom) {
                    RideShareDetails()
                }
            } compactLeading: {
                AppLogo()
            } compactTrailing: {
                ETAView()
            } minimal: {
                ETAView()
            }
        }
        .supplementalActivityFamilies([.small, .medium])
    }
}
```

You can opt-in to give people the ability to open your Watch app from your Live Activity. In the Build Settings for your Watch app target, add a value for the `Supports Launch for Live Activity Attribute Types` key in the `Info.plist` section. To launch your Watch app for all your Live Activities, leave the value empty. To launch for specific Live Activities, add an item for each ActivityAttributes conforming type that launches your Watch app.

### Set custom content margins

Limiting the content you display is key to offering glanceable, easy-to-read Live Activities. Aim to use the system’s default content margins for your Live Activities and only show content that’s relevant to the person viewing it. However, you may want to change the system’s default content margin to display more content or provide a custom user interface that matches your app. To set custom content margins, use contentMargins(_:_:for:). The following example results in a margin of eight points for the trailing edge of an expanded Live Activity.

```
struct AdventureActivityConfiguration: Widget {
    var body: some WidgetConfiguration {
        ActivityConfiguration(for: AdventureAttributes.self) { context in
            // Create the presentation that appears on the Lock Screen and as a
            // banner on the Home Screen of devices that don't support the
            // Dynamic Island.
            // ...
        } dynamicIsland: { context in
            // Create the presentations that appear in the Dynamic Island.
            DynamicIsland {
                // Create the expanded presentation.
                // ...
            } compactLeading: {
                // Create the compact leading presentation.
                // ...
            } compactTrailing: {
                // Create the compact trailing presentation.
                // ...
            } minimal: {
                // Create the minimal presentation.
                // ...
            }
            .contentMargins(.trailing, 8, for: .expanded)
            .contentMargins(.all, 20, for: .expanded)
        }
    }
}
```

If you repeatedly use the `contentMargins(_:_:for:)` modifier, the system uses the innermost specified values for a mode.

Note

Avoid placing content too close to the edges of the Dynamic Island.

### Use custom colors

Live Activities in the Dynamic Island use a black background color with white text. Use the keylineTint(_:) modifier to apply a subtle tint color to the border of the Dynamic Island when the device is in Dark Mode and change text color as needed.

Note

You can’t change the background color of Live Activities in the Dynamic Island.

By default, the Lock Screen presentation — including the banner that appears on devices that don’t support the Dynamic island — uses a solid white background color in Light Mode and a solid black background color in Dark Mode. To set a custom background color for the Lock Screen presentation, use the activityBackgroundTint(_:) modifier. Be sure to choose a color that works well in both Dark or Light Mode or use different background colors that best fit each appearance. To set the translucency of the custom background color, use the opacity(_:) view modifier or specify an opaque background color.

If you choose a custom background color for the Lock Screen presentation, use the activitySystemActionForegroundColor(_:) view modifier to customize the text color of the auxiliary button that allows people to end the Live Activity on the Lock Screen.

Note

On devices that include an Always-On display, the system dims the screen to preserve battery life and renders Live Activities on the Lock Screen as if in Dark Mode. Use SwiftUI’s isLuminanceReduced environment value to detect reduced luminance on devices with an Always-On display and use colors and images that look great with reduced luminance.

### Create a deep link into your app

People tap a Live Activity to launch your app. To improve the user experience, you can use widgetURL(_:) to create a deep link into your app from the Lock Screen, compact leading, compact trailing, and minimal presentations. When the compact leading and trailing presentations are visible, make sure both link to the same screen in your app.

The expanded presentation offers additional options to create deep links into your app for more utility using SwiftUI’s Link.

If you don’t explicitly provide a deep link into your app with widgetURL(_:) or Link and a person interacts with it, the system opens the containing app and passes an, the system launches your app and passes an NSUserActivity to onContinueUserActivity(_:perform:), application(_:continue:restorationHandler:), or application(_:continue:restorationHandler:). Implement the appropriate callback and check whether the `NSUserActivity` object’s activityType is NSUserActivityTypeLiveActivity. Then, add code to open a screen in your app that fits the context of the active Live Activity.

For additional information about deep linking into your app, refer to Linking to specific app scenes from your widget or Live Activity.

### Add Buttons or Toggles

Like widgets, starting with iOS 17 and iPadOS 17, Live Activities can contain SwiftUI buttons and toggles to provide quick actions. For example, a food-ordering app might show a button in its Live Activity that people tap to check in at a restaurant when they pick up a takeout order.

To add a toggle or button to a Live Activity, adopt the App Intents framework and use the initializers for Button and Toggle that take an app intent. For more information about using toggles and buttons in widget extensions, including for Live Activities, refer to WidgetKit.

### Provide accessibility labels

Designing with accessibility in mind is a foundational principle when creating an app. It also applies to Live Activities. To allow people to customize how they interact with your Live Activity and to make sure VoiceOver for your Live Activity works correctly, add accessibility labels for the SwiftUI views you create for each Live Activity presentation. For more information, refer to Adding accessible descriptions to widgets and Live Activities.

### Make sure Live Activities are available

Live Activities are available on iPhone and iPad. If your app is available on additional platforms and offers a widget extension, make sure Live Activities are available at runtime. Additionally, people can choose to deactivate Live Activities for an app in the Settings app.

To refer to if Live Activities are available and if a person allowed your app to use Live Activities:

- Use areActivitiesEnabled to synchronously determine whether to show a user interface in your app for starting a Live Activity.

- Receive asynchronous user authorization updates by observing any user authorization changes with the activityEnablementUpdates stream and respond to them accordingly.

Note

An app can start several Live Activities, and a device can run Live Activities from several apps — the exact number may depend on a variety of factors. In addition to making sure Live Activities are available, always handle any errors gracefully when starting, updating, or ending a Live Activity. For example, starting a Live Activity may fail because a person’s device may have reached its limit of active Live Activities.

### Configure the Live Activity

Before you can start a Live Activity in your app, configure it with an ActivityContent structure. The activity content encapsulates the ActivityAttributes and additional configuration information:

- The staleDate tells the system when the Live Activity content becomes outdated.

- The relevanceScore determines which of your Live Activities appears in the Dynamic Island and the order of your Live Activities on the Lock Screen.

While setting the staleDate is optional, it’s helpful when you want to ensure your Live Activity doesn’t display outdated content. At the specified date, the activityState changes to ActivityState.stale and isStale changes to `true`. Access isStale to monitor the activity state and respond to outdated Live Activities that haven’t received updates. For example, while a person has network connectivity, a sports app could update the Live Activity with the latest game information and advance the stale date. If a person enters an area without network connectivity, the app can’t update the Live Activity with new information and an advanced stale date. Eventually, the Live Activity becomes stale and displays text to indicate that the displayed information is outdated. On the next app launch or when it performs background tasks, the app can also respond to the ActivityState.stale state.

If your app starts more than one Live Activity, provide a relevance score to determine the order of your Live Activities on the Lock Screen and which of your Live Activities appears in the Dynamic Island:

- If you don’t provide a relevance score or if Live Activities have the same relevance score, the system shows the first Live Activity you started in the Dynamic Island.

- If you use different relevance scores, the system shows the Live Activity with the highest relevance score in the Dynamic Island.

The system expects relative values for the relevance score. Assign a higher value for an important Live Activity content update — for example, a score of `100` — and use lower values for less important Live Activity content updates — for example, `50`.

Note

Keep track of the relevance scores you assign for each ongoing Live Activity so you can change the order of them as needed with each Live Activity update.

### Start the Live Activity

You start a Live Activity in your app’s code while the app is in the foreground with the request(attributes:content:pushType:) function. Pass the ActivityAttributes and ActivityContent objects you created to it and, if you implement ActivityKit push notifications, the `pushType` parameter.

The following example from the Emoji Rangers: Supporting Live Activities, interactivity, and animations app creates the initial attributes and content state for the Emoji Rangers Live Activity.

```
if ActivityAuthorizationInfo().areActivitiesEnabled {
    do {
        let adventure = AdventureAttributes(hero: hero)
        let initialState = AdventureAttributes.ContentState(
            currentHealthLevel: hero.healthLevel,
            eventDescription: "Adventure has begun!"
        )

        let activity = try Activity.request(
            attributes: adventure,
            content: .init(state: initialState, staleDate: nil),
            pushType: .token
        )

        self.setup(withActivity: activity)
    } catch {
        errorMessage = """
                   Couldn't start activity
                   ------------------------
                   \(String(describing: error))
                   """

        self.errorMessage = errorMessage
    }
}
```

Your app can only start Live Activities while it’s in the foreground. However, you can update or end a Live Activity from your app while it runs in the background — for example, by using Background Tasks.

Additionally, you can enable Live Activity updates with ActivityKit push notifications. Pass `.token` as a value the `pushType` parameter as shown in the example above, and implement your remote notification server. Starting with iOS 17.2 and iPadOS 17.2, you can also start Live Activities with ActivityKit push notifications. For more information on using ActivityKit push notifications, refer to Starting and updating Live Activities with ActivityKit push notifications.

### Update the Live Activity

When you start a Live Activity from your app, update the data that appears in the Live Activity using the update(_:) function of the Activity object you received when you started the Live Activity. To retrieve your app’s active Live Activities, use activities.

For important updates, use the update(_:alertConfiguration:) function to display an alert on iPhone, iPad, and a paired Apple Watch that tells a person about new Live Activity content. For example, the Emoji Rangers: Supporting Live Activities, interactivity, and animations app updates its Live Activity using an alert configuration to display an alert that lets people know that the hero has been knocked down:

```
guard let activity = currentActivity else {
    return
}

var alertConfig: AlertConfiguration? = nil
let contentState: AdventureAttributes.ContentState
if alert {
    let heroName = activity.attributes.hero.name

    alertConfig = AlertConfiguration(
        title: "\(heroName) has been knocked down!",
        body: "Open the app and use a potion to heal \(heroName).",
        sound: .default
    )

    contentState = AdventureAttributes.ContentState(
        currentHealthLevel: 0,
        eventDescription: "\(heroName) has been knocked down!"
    )
} else {
    contentState = AdventureAttributes.ContentState(
        currentHealthLevel: Double.random(in: 0...1),
        eventDescription: self.getEventDescription(hero: activity.attributes.hero)
    )
}

await activity.update(
    ActivityContent(
        state: contentState,
        staleDate: Date.now + 15,
        relevanceScore: alert ? 100 : 50
    ),
    alertConfiguration: alertConfig
)
```

Note

The size of the updated data can’t exceed 4KB in size.

On Apple Watch, the system uses the `title` and `body` attributes for the alert. On iPhone and iPad, the system doesn’t show a regular alert but instead shows the expanded Live Activity in the Dynamic Island or the Lock Screen presentation as a banner on devices without the Dynamic Island.

### Animate content updates

When you define the user interface of your Live Activity, the system ignores any animation modifiers — for example, withAnimation(_:_:) and animation(_:value:) — and uses the system’s animation timing instead. However, the system performs some animation when the dynamic content of the Live Activity changes. Text views animate content changes with blurred content transitions, and the system animates content transitions for images and SF Symbols. If you add or remove views from the user interface based on content or state changes, views fade in and out. Use the following view transitions to configure these built-in transitions: opacity, move(edge:), slide, push(from:), or combinations of them. Additionally, request animations for timer text with numericText(countsDown:).

Starting with iOS 17 and iPadOS 17, you can animate data changes in your Live Activity with functions that give you more control over animation timing. For example, you can use timingCurve(_:duration:) to create an animation with a custom timing curve. For more information on SwiftUI animations, refer to Animation.

Note

On devices that include an Always-On display, the system doesn’t perform animations to preserve battery life in Always On. Make sure to use SwiftUI’s isLuminanceReduced environment value to detect reduced luminance before animating content changes.

### End the Live Activity

Always end a Live Activity after the associated task or live event ends. A Live Activity that ended remains on the Lock Screen until the person removes it or the system removes it automatically. The automatic removal depends on the dismissal policy you provide to the end(_:dismissalPolicy:) function. Always include an updated Activity.ContentState to ensure the Live Activity shows the latest and final content update after it ends. This is important because the Live Activity can remain visible on the Lock Screen for some time after it ends.

The following example shows how the Emoji Rangers: Supporting Live Activities, interactivity, and animations app ends its Live Activity and sets a custom dismissal policy based on a setting in the app:

```
func endActivity(dismissTimeInterval: Double?) async {
    guard let activity = currentActivity else {
        return
    }

    let hero = activity.attributes.hero

    let finalContent = AdventureAttributes.ContentState(
        currentHealthLevel: 1.0,
        eventDescription: "Adventure over! \(hero.name) is taking a nap."
    )

    let dismissalPolicy: ActivityUIDismissalPolicy
    if let dismissTimeInterval = dismissTimeInterval {
        if dismissTimeInterval 

With the default dismissal policy, the Live Activity appears on the Lock Screen for some time after it ends to allow a person to glance at their phone to refer to the latest information. A person can choose to remove the Live Activity at any time, or the system removes it automatically four hours after it ended.

To immediately remove the Live Activity that ended from the Lock Screen, use immediate. Alternatively, use after(_:) to specify a date within a four-hour window. While you can provide any date, the system removes the ended Live Activity after the given date or after four hours from the moment the Live Activity ended — whichever comes first.

A person can remove your Live Activity from their Lock Screen at any time. This ends the Live Activity, but it doesn’t end or cancel the person’s action that started it. For example, a person may remove the Live Activity for their pizza delivery from the Lock Screen, but this doesn’t cancel the pizza order.

Note

When a person or the system removes a Live Activity, its ActivityState changes to ActivityState.dismissed.

### Update or end your Live Activity with a push notification

In addition to updating and ending a Live Activity from your app with ActivityKit, update or end a Live Activity with an ActivityKit push notification that you send from your server to the Apple Push Notification service (APNs). Starting with iOS 17.2 and iPadOS 17.2, ActivityKit push notifications can also start Live Activities. To learn more about using ActivityKit push notifications, refer to Starting and updating Live Activities with ActivityKit push notifications.

### Keep track of updates

When you start a Live Activity, ActivityKit returns an Activity object. In addition to the id that uniquely identifies each activity, the Activity offers sequences to observe content, activity state, and push token updates. Use the corresponding sequence to receive updates in your app, keep your app and Live Activities in sync, and respond to changed data:

- To observe changes to ongoing Live Activities and to asynchronously access a Live Activity when you start it, use activityUpdates.

- To observe the state of an ongoing Live Activity — for example, to determine whether it’s active or has ended — use activityStateUpdates.

- To observe changes to the dynamic content of a Live Activity, use contentUpdates.

- To observe changes to the push token of a Live Activity, use pushTokenUpdates.

The following example shows how the Emoji Rangers: Supporting Live Activities, interactivity, and animations app tracks updates its content for ongoing Live Activities and updates its adventure view accordingly:

```
// Observe updates for ongoing Live Activities.
Task {
    for await content in activity.contentUpdates {
        self.updateAdventureView(content: content)
    }
}
```

### Observe active Live Activities

Your app can start more than one Live Activity. For example, a sports app may allow a person to start a Live Activity for each live sports game they’re interested in. If your app starts multiple Live Activities, keep track of ongoing Live Activities for your app using the activities property to make sure your app is aware of all ongoing Live Activities that ActivityKit tracks. Another use case for fetching all activities is to maintain Live Activities that are in progress and make sure you don’t keep any activities running for longer than needed. For example, the system may stop your app, or your app may crash while a Live Activity is active. When the app launches the next time, check if any activities are still active, update your app’s stored Live Activity data, and end any Live Activity that’s no longer relevant.

### Start and stop Live Activities from App Intents

The App Intents framework enables you to extend your app’s custom functionality to support system-level services like Siri and the Shortcuts app, as well as the functionality to start a Live Activity. For example, a sports app could expose functionality to start a Live Activity for a person’s favorite sports team with the Shortcuts app or Siri.

Starting a Live Activity from an app intent is almost the same as adopting App Intents to expose other functionality in your app:

1.  Adopt the App Intents framework as described in Making actions and content discoverable and widely available.

2.  When you implement your app intent that starts the Live Activity, make sure it inherits from LiveActivityStartingIntent.

3.  In your LiveActivityStartingIntent implementation, add code to start the Live Activity.

## See Also

### Live Activity implementation

Starting and updating Live Activities with ActivityKit push notifications

Use ActivityKit to receive push tokens and to remotely start, update, and end your Live Activity with ActivityKit notifications.

Adding accessible descriptions to widgets and Live Activities

Describe the interface elements of your widgets and Live Activities to help people understand what they represent.

class Activity

The object you use to start, update, and end a Live Activity.

Emoji Rangers: Supporting Live Activities, interactivity, and animations

Offer Live Activities, controls, animate data updates, and add interactivity to widgets.

NSSupportsLiveActivities

A Boolean value that indicates whether an app supports Live Activities.

NSSupportsLiveActivitiesFrequentUpdates

A Boolean value that indicates whether an app can update its Live Activities frequently.

