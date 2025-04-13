

- WatchKit
-  Using extended runtime sessions 

Article

# Using extended runtime sessions

Create an extended runtime session that continues running your app after the user stops interacting with it.

## Overview

An app running on Apple Watch normally transitions to the background and becomes suspended when the user lowers their wrist. However, your app can use both background sessions and extended runtime sessions to continue running after the user stops interacting with it.

With background sessions, your app continues to run in the background, but the sessions can only monitor workouts, track the user’s location, or play audio files. Extended runtime sessions, on the other hand, expand on this ability and give your app several different session types to choose from. Not all of these sessions run in the background. Some keep your app active and running as the frontmost app instead. Extended runtime sessions support the following session types:

Self care  
Guide users through relatively brief activities. These activities focus on the user’s emotional well-being or health, such as brushing their teeth.

Mindfulness  
Help users start and end silent meditation sessions. For walking meditation, consider using HKWorkoutSession instead. Similarly, if your app plays audio during the entire meditation session, there’s no reason to use a WKExtendedRuntimeSession. The background audio mode provides additional runtime as long as the audio plays. For more information, see Playing Background Audio.

Physical therapy  
Guide users through stretching, strengthening, or range-of-motion exercises. If the physical therapy activity is strenuous—for example, riding an exercise bike—consider using an HKWorkoutSession instead.

Smart alarm  
Schedule a window of time to monitor the user’s heart rate and motion. The app uses this information to determine the optimal time to play an alarm, usually to wake the user from sleep.

Select a session type based on the app’s intended use—not based on the features that the session provides. Extended runtime sessions let the app continue to communicate with a Bluetooth device, process data, or play sounds or haptics, even after the watch’s screen turns off.

Important

To maintain high performance on Apple Watch, limit the amount of work performed during an extended runtime session. If your app sustains high CPU usage over a period of time, the system may cancel the session (see WKExtendedRuntimeSessionErrorCode.exceededResourceLimits). Use Xcode’s CPU report tool or the time profiler in Instruments to test and minimize your app’s CPU usage.

### Set Up the Session

Before starting an extended runtime session, enable your WatchKit extension’s Background Modes capability and select your app’s session type (see Figure 1). Each app can only support one type of extended runtime session, although it’s possible to support other background modes in combination with extended runtime.

A physical therapy app, for example, might use a WKExtendedRuntimeSession for range-of-motion exercises and an HKWorkoutSession for vigorous cross-training. Using separate sessions keeps the range-of-motion exercise from impacting the user’s Move and Exercise rings, but the user still gets full credit for the cross-training.

To set up the session, instantiate a WKExtendedRuntimeSession object, and assign your delegate. The system automatically creates a session based on the session type specified in your Background Modes capabilities.

```
// Create the session object.
session = WKExtendedRuntimeSession()

// Assign the delegate.
session.delegate = self
```

Implement the WKExtendedRuntimeSessionDelegate methods to track your session.

```
// MARK:- Extended Runtime Session Delegate Methods
func extendedRuntimeSessionDidStart(_ extendedRuntimeSession: WKExtendedRuntimeSession) {
    // Track when your session starts.
}

func extendedRuntimeSessionWillExpire(_ extendedRuntimeSession: WKExtendedRuntimeSession) {
    // Finish and clean up any tasks before the session ends. 
}

func extendedRuntimeSession(_ extendedRuntimeSession: WKExtendedRuntimeSession, didInvalidateWith reason: WKExtendedRuntimeSessionInvalidationReason, error: Error?) {
    // Track when your session ends.
    // Also handle errors here.
}
```

Finally, start your session. For most session types, you start the session immediately by calling start(). For alarm sessions, you can schedule the session to start any time within the next 36 hours by calling start(at:).

```
session.start()
```

You must always start or schedule the extended runtime session when your app state is in the WKApplicationState.active state.

The session automatically stops when its allotted time expires. You can track the time remaining using its expirationDate property. You can also stop a session by calling invalidate().

For sessions started with start(at:), you can only call invalidate() when the app is active. For all other sessions, you can call invalidate() to end a session at any time.

```
@IBAction func stopButton() {
    session.invalidate()
}
```

### Understand Session Behaviors

Extended runtime sessions gain the following features, based on the session type.

| Session type     | Runtime    | Schedulable | Time limit |
|------------------|------------|-------------|------------|
| Self care        | Frontmost  | No          | 10 minutes |
| Mindfulness      | Frontmost  | No          | 1 hour     |
| Physical therapy | Background | No          | 1 hour     |
| Smart alarm      | Background | Yes         | 30 minutes |

*Frontmost* sessions continue to run in the foreground. The watch screen doesn’t need to remain on to keep your app alive. The session continues until the time limit expires, your app invalidates the session, or the user explicitly leaves your app (for example, by pressing the digital crown or switching to a different app).

*Background* sessions continue to run in the background, even if the user dismisses the app or launches another app. Background sessions continue to run until the time limit expires, or your app invalidates the session.

Finally, s_chedulable\_ sessions can start any time within the next 36 hours. You must schedule the session by calling start(at:) while your app is in the WKApplicationState.active state. The system can then suspend or terminate your app without affecting the session. The system relaunches your app as needed to handle a scheduled session, calling your extension delegate’s handle(_:) method. If you don’t set the session’s delegate in the handle(_:) method, the system ends the session. Additionally, you can only schedule one session at a time; if you need to reschedule a session, invalidate the current session, and schedule a new one.

After the session starts, the app continues to run in the background until the time limit expires, or your app invalidates the session. During the session, your app must trigger the alarm by calling the session’s notifyUser(hapticType:repeatHandler:) method. If your app isn’t active, playing the haptic displays a system alarm alert to the user.

If you fail to play a haptic during the session, the system displays a warning and offers to disable future sessions.

## See Also

### Runtime management

Background execution

Manage background sessions and tasks.

Life cycles

Receive and respond to life-cycle notifications.

class WKExtendedRuntimeSession

A session that continues to run your app after the user has stopped interacting.

Interacting with Bluetooth peripherals during background app refresh

Keep your complications up-to-date by reading values from a Bluetooth peripheral while your app is running in the background.

