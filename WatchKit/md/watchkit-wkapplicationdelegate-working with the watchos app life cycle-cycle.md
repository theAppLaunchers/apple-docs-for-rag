

- WatchKit
- WKApplicationDelegate
-  Working with the watchOS app life cycle 

Article

# Working with the watchOS app life cycle

Learn how the watchOS app life cycle operates and responds to life cycle notification methods.

## Overview

WatchKit reports changes in your app’s execution state to your extension delegate object. State changes correspond to major events in the lifetime of your app, and the state changes in a watchOS app are analogous to the state changes of an iOS app. For each state change, perform relevant tasks, such as loading shared resources and configuring your initial user interface. The following table lists the possible state of the app and the implications for your app.

| State | Description |
|----|----|
| Not running | The watchOS app isn’t running. The user hasn’t launched the watchOS app, or the system suspended and then purged the app. |
| Inactive | The watchOS app is running in the foreground, but isn’t receiving actions from controls or gestures; however, it may be executing other code. A newly launched app usually stays in this state only briefly as it transitions to the active state. An active app that transitions to this state should quiet itself and prepare to transition to the background. |
| Active | The watchOS app is running in the foreground and receiving actions from controls and gestures. This is the normal mode for apps running onscreen. |
| Background | The system has given the watchOS app a small amount of background execution time. The system gives apps background execution time when running a background session, when performing background tasks, and before suspending the app.  Because the system can purge suspended apps without warning, use the extension delegate’s applicationDidEnterBackground() method to save any data you need to re-create your app’s current state. If needed, you can request additional background execution time by calling the ProcessInfo class’s performExpiringActivity(withReason:using:) method. |
| Suspended | The app is in memory but isn’t executing code. The system suspends apps that are in the background and don’t have any pending tasks to complete. The system may purge suspended apps at any time to make room for other apps. The system silently purges suspended apps. The suspended apps don’t wake, and don’t receive any notifications before the system purges them.  The system tries to keep frequently used apps in memory, allowing them to resume as quickly as possible. Specifically, the system preserves the most recently executed app, any apps that are in the Dock, and any apps that have a complication on the currently active watch face. If memory constraints force the system to purge one of these apps, the system relaunches the app as soon as more memory becomes available. |

The following diagram shows the state changes that occur for a watchOS app and the delegate methods that watchOS calls when those changes occur.

In the preceding diagram:

- **Transition A.** When transitioning from not running to either the inactive or background state, the system calls the extension delegate’s applicationDidFinishLaunching() method.

- **Transition B.** When transitioning between the inactive and active states, the system calls either the applicationDidBecomeActive() or applicationWillResignActive() method.

- **Transition C.** When transitioning between the background and inactive states, the system calls either the applicationWillEnterForeground() or applicationDidEnterBackground() method.

Except for applicationDidFinishLaunching(), the system only calls the extension delegate’s life cycle methods for the watchOS app’s main interface. The system doesn’t call the delegate methods when it displays any other supplementary interfaces. For example, it doesn’t call the methods when it launches the app to update complications or to display custom notification interfaces. For notifications, use the notification controller’s willActivate() and didDeactivate() methods to track the state of the interface.

### Step through common state transitions

The watch app runs in different states depending on the app’s current context. Also, there’s no direct relationship between the app’s state and the interface’s state. For example, the app may be inactive while the interface is active. The following table shows the app and interface states in most common situations.

| Situation | App state | Interface state |
|----|----|----|
| Running onscreen | Active | Active |
| Running in the dock | Inactive, and the extension’s isApplicationRunningInDock property is true | Active, shown in the dock. |
| Running as the frontmost app | Inactive | Inactive |
| Displaying a dynamic notification interface | Inactive or background | Notification interface is active |
| Processing a snapshot background task | Background | Active, but not shown onscreen |
| Processing another background task | Background | Inactive |
| Running a background session | Background | Inactive |

When transitioning between states, the exact flow depends on the app’s starting and ending conditions, as well as other considerations — for example, if the app has a complication in the current watch face, or if the app is currently the frontmost app, and so on. Some of the most common transitions include when an app launches, goes to the background, or resumes.

The app launches when it isn’t running, and the user explicitly starts the app — for example tapping the app icon on the home screen.

1.  The app\_ \_transitions to the WKApplicationState.inactive state. The system calls the extension delegate’s applicationDidFinishLaunching() method.

2.  The system instantiates the initial interface controller and calls its awake(withContext:) method.

3.  The app transitions to the WKApplicationState.active state. The system calls the extension delegate’s applicationDidBecomeActive() method.

4.  The system calls the initial interface controller’s willActivate() method.

5.  *The app* appears onscreen. The system calls the initial interface controller’s didAppear() method.

The app goes to the background when it’s running onscreen in the WKApplicationState.active state, and the user lowers their arm or the screen turns off. If the user explicitly closes the app, by pressing the digital crown or covering the screen, the app doesn’t become the frontmost app, and doesn’t remain in the inactive state, but transitions quickly to the background instead.

1.  *The system* calls the extension delegate’s applicationWillResignActive() method.

2.  *The app* transitions to the WKApplicationState.inactive state. The app remains in this state as long as it’s the frontmost app (by default, 2 minutes).

3.  *The app* transitions to the WKApplicationState.background state. *The system* calls the extension delegate’s applicationDidEnterBackground() method.

4.  *The system* calls the presented interface controller’s didDeactivate() method.

5.  *The system* suspends the app.\*\*\*\*

The app resumes when the app is running in the background, or is suspended, and the user activates the app, for example, by tapping its complication on the active watch face.

1.  If suspended but in memory, *the app* restarts in the WKApplicationState.background state.

2.  *The system* calls the extension delegate’s applicationWillEnterForeground() method.

3.  *The app* transitions to the WKApplicationState.active state. *The system* calls the extension delegate’s applicationDidBecomeActive() method.

4.  *The system* calls the initial interface controller’s willActivate() method.

### Receive background data

When the system receives background data, it may not immediately wake the watchOS app to process that data. Instead, it may delay delivery of the data to preserve battery life.

If the app is currently running—either active and onscreen, or inactive and the frontmost app—the system immediately delivers the data to the app. If the app is in the background, the system wakes the app within 10 minutes to deliver the data.

## See Also

### Monitoring state changes

static func main()

Provides the top-level entry point for an app.

func applicationDidFinishLaunching()

Tells the delegate that the launch process is almost done and the app is almost ready to run.

func applicationDidBecomeActive()

Tells the delegate that the watchOS app is visible and processing events.

func applicationWillResignActive()

Tells the delegate that the system is about to deactivate the watchOS app.

func applicationWillEnterForeground()

Tells the delegate that the app is about to transition from the background to the foreground.

func applicationDidEnterBackground()

Tells the delegate that the app has transitioned from the foreground to the background.

func deviceOrientationDidChange()

Tells the delegate that the device’s orientation has changed.

