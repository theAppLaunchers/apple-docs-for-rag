

- watchOS apps
-  Designing your app for the Always On state 

Article

# Designing your app for the Always On state

Customize your watchOS app’s user interface for continuous display.

## Overview

The launch of watchOS 6 introduced the Always On state. Supported devices continued to display the time, even when the user isn’t actively interacting with the watch; however, when running an app, the system blurs the app’s user interface and displays the time over it.

In watchOS 8, Always On expands to include your apps. Apple Watch continues to display your app’s user interface as long as it’s either the frontmost app or running a background session. To preserve battery life, the system updates the user interface at a much lower frequency than when running in the foreground. It also dims the watch.

Even though your app is inactive or running in the background, the system continues to update and monitor many of the user interface elements. For example, when displaying dates and times, using Text.DateStyle values like relative, offset, and timer, the system automatically updates the Text view while in Always On.

Additionally, any controls in the user interface remain interactive. Users can tap buttons, toggle switches, or select items from a list. When the user interacts with a control, the system runs the associated action and transitions your app back to the active state.

Note

Always On isn’t available on Apple Watch SE or Apple Watch Series 4 and earlier. For these devices, the screen turns off when the app transitions to the background or inactive states.

Apps compiled for watchOS 8 and later have Always On enabled by default. You can disable this feature by setting the WKSupportsAlwaysOnDisplay key to false in the WatchKit Extension’s `Info.plist` file. Users can also disable Always On for the entire device or on a per-app basis by choosing Settings \> Display & Brightness \> Always On.

### Understand frontmost app behavior

By default, when the user lowers their wrist or stops interacting with their watch, your app transitions to the inactive state. The system continues to display your app’s user interface as long as your app remains the frontmost app (usually two minutes) before transitioning to the background and becoming suspended. If the user dismisses the app (for example, by pressing the Digital Crown or by covering the screen), the app transitions immediately to the background and doesn’t become the frontmost app.

Users can set the amount of time that apps remain the frontmost app by changing the settings at Settings \> General \> Wake Screen \> Return to Clock. They can also specify a custom time for individual apps from the Wake Screen. In watchOS 8 and later, apps can remain in the frontmost app state for a maximum of 1 hour.

When the app is inactive, the user interface doesn’t update by default. However, you can use a TimelineView to schedule periodic updates. For more information, see Updating watchOS apps with timelines.

### Update the display during background sessions

Apps running a background session, such as a workout session or background audio session, remain onscreen as long as the session is active. Unlike frontmost apps, apps running a background session can continue to update their user interface; however, to save battery life, the system reduces the update frequency.

For the best user experience when the app transitions to the background, pause any animation and show the final state (or a good static image), and remove any subsecond updates. For example, when the workout app is running in the foreground, the duration shows hundredths of a second, and the BPM row shows an animated heart beat. When it transitions to the background, the app displays a static heart image and the duration only shows time to the nearest second.

For animation or updates driven by a TimelineView, check the view’s cadence and update the appearance to match. For more information on timelines, see Updating watchOS apps with timelines.

```
TimelineView(PeriodicTimelineSchedule(from: Date(), by: 1.0/60.0)) { context in
    switch context.cadence {
    case .live:
        // Display up to 60 updates per second.
    case .seconds:
        // Only show items that update approximately once per second.
    case .minutes:
        // Only show items that update approximately once per minute.
    @unknown default:
       fatalError("*** Received an unknown cadence: \(context.cadence) ***")
    }
}
```

For other views, monitor the app’s scenePhase environment variable, and hide or stop subsecond updates when it becomes ScenePhase.inactive or ScenePhase.background.

```
@Environment(\.scenePhase) private var scenePhase

var body: some View {
    if scenePhase == .active {
        // Animation and subsecond updates here.
    } else {
        // Low-frequency updates here.
    }
}
```

### Hide sensitive information

Because displayed information may be visible to casual observers, be sure to hide any sensitive data while your app is in Always On. Add the privacySensitive(_:) view modifier to blur out specific user interface elements during Always On.

```
Text("Account Number:")
    .font(.headline)
Text(accountNumber)
    .privacySensitive()
```

Or access the redactionReasons environment variable.

```
@Environment(\.redactionReasons) var redactionReasons
```

Check if this variable contains the privacy value. If it does, eliminate or obscure any sensitive data.

```
if !redactionReasons.contains(.privacy) {
    Text("Balance:")
        .font(.headline)
    Text(balance)
}
```

The resulting user interface displays the private data while the app is running in the foreground.

But the interface obscures sensitive data, such as the account number and balance, when the app is in the Always On state.

To protect the user’s privacy, always hide any highly sensitive information, such as financial information or health data. For information that may or may not be sensitive, such as incoming messages or appointments, default to showing the information. If the user has any concerns, they can disable Always On on a per-app basis.

### Customize the reduced luminance appearance

To preserve battery life, the system dims the screen during Always On. The system determines the screen’s overall luminance by comparing the ratio of lit pixels to dark pixels. It then reduces the overall brightness to an appropriate level.

Many system controls also automatically update their appearance during Always On. For example, the List view automatically dims the background for the CarouselListStyle.

Many apps can use the system’s default Always On appearance. For example, if your view is mostly black and uses system controls, you may not need to change anything. However, you can customize the appearance during Always On to highlight glanceable, important information in your user interface.

For example, you may consider replacing large blocks of bright content with stroked outlines and dimmed interiors, as shown on the Numerals Duo watch face.

You can also dim or remove nonessential information. To customize your interface, use the isLuminanceReduced environment variable.

```
@Environment(\.isLuminanceReduced) var isLuminanceReduced
```

You can then use this value to modify your user interface, as needed.

```
Text("Hello!")
    .font(.title)
    .fontWeight(.bold)
    .opacity(isLuminanceReduced ? 0.5 : 1.0)
```

The resulting interface displays the title text at full brightness when active.

Then it dims the title in Always On. Because the ratio of lit to dark pixels is low, the system doesn’t need to make any other changes to the view.

### Preview both interfaces in Xcode

You can preview both the regular and Always On interfaces in Xcode. To see the Always On interface, set the isLuminanceReduced and redactionReasons environment variables in the preview.

```
struct ContentView_Previews: PreviewProvider {
    static var previews: some View {
        Group {
            ContentView()
            ContentView()
                .environment(\.isLuminanceReduced, true)
                .environment(\.redactionReasons, [.privacy])
        }
    }
}
```

The resulting preview shows both the regular and the Always On interfaces.

Note

The system doesn’t automatically dim the user interface when previewing in Xcode. To see how the system automatically dims the user interface, you must test it on a device or in the simulator.

### Test Always On in the Simulator

Xcode supports Always On in the simulator. Simply click the Toggle Always On button in the status bar to test.

You can view any changes to your user interface related to privacy, reduced luminance, or transitioning to an inactive state.

## See Also

### Related Documentation

WKSupportsAlwaysOnDisplay

A Boolean value that determines whether the system displays the app in the Always On state.

### User interface

Building a productivity app for Apple Watch

Create a watch app to manage and share a task list and visualize the status with a chart.

Supporting multiple watch sizes

Customize the layout of your user interface to support all Apple Watch sizes.

Setting the app’s accent color

Set your app’s accent color.

