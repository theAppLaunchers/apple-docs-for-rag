

- Xcode
- Performance and metrics
-  Reducing terminations in your app 

Article

# Reducing terminations in your app

Minimize how frequently the system stops your app by addressing common termination reasons.

## Overview

Terminations are part of the app lifecycle, when the system stops your process. You can significantly reduce terminations by fixing bugs and lowering your app’s resource consumption; however, terminations are expected and you cannot fully eliminate them. The system uses terminations to prioritize resources needed to keep the foreground user experience fluid.

When the system terminates your app, your app must re-launch the next time a user activates it. A re-launch is much slower than re-activating your app.

View Termination data using the Xcode Organizer or collect data in your app using MetricKit’s MXAppExitMetric.

For more information about debugging your terminations, see the following WWDC session video: developer.apple.com/videos/play/wwdc2020/10078.

### Understand termination reasons

The system stops your app when it encounters any of the following issues.

- Aborts (Abnormal Exits). An abort happens when your process calls `abort()`. This commonly occurs when your app encounters uncaught exceptions or failed `assert()` calls, often through a framework that your app uses. An abort makes use of the SIGABRT signal. Aborts are crashes.

- Memory Limit. On iOS, the system attempts to provide foreground apps as much memory as possible. If your app attempts to use more memory than the system can provide, the system terminates it.

- Bad Access. A Bad Access termination happens when your app attempts to access invalid memory; for example, by deferencing null pointers or by attempting to index out of bounds on an array. Bad Access terminations are crashes.

- Illegal Instruction. An Illegal Instruction termination happens when your app attempts to execute an instruction that the system cannot interpret. Illegal Instruction terminations are crashes.

- App Watchdog. An App Timeout happens when your app takes too long to launch. The system gives a lenient amount of time to launch, and a timeout is generally indicative of your app getting stuck on launch. Many users will quit your app before this limit is hit, and those quits will not be considered an App Timeout. macOS apps do not have a launch time limit.

- Memory Pressure. As part of the normal app lifecycle, iOS & watchOS terminate apps when the system requires more memory than is currently available. The system most often terminates apps in the background when a foreground app needs more memory. Reduce the frequency of memory pressure terminations for your app by lowering your memory at suspension. You can see memory at suspension in the Xcode Organizer. Because you cannot remove all memory pressure terminations, ensure that your app has proper state restoration to provide a fluid user experience.

To resolve terminations that are crashes, view the stack trace for the crash in the Crashes Organizer in Xcode. For more information about diagnosing and resolving a crash, see Diagnosing Issues Using Crash Reports and Device Logs .

### Background termination reasons

Some termination reasons only apply while your app is in the background:

- Task Timeout. The system allows your app to continue executing in the background, after the user has placed the app in the background, through the use of the beginBackgroundTask API. If your app does not finish its work in the allotted time, the system will terminate it with the Task Timeout reason.

- File Lock. A File Lock termination happens when your app continues to hold a lock on a shared file held in your AppGroup when the user put your app in the background. The system performs this termination to avoid blocking on a lock that your app may never release.

## See Also

### Responsiveness

Analyzing responsiveness issues in your shipping app

Identify responsiveness issues your users encounter, and use the hang and hitch data in Xcode Organizer to determine which issues are most important to fix.

Improving app responsiveness

Create a user experience that feels responsive by removing hangs and hitches from your app.

Understanding user interface responsiveness

Make your app more responsive by examining the event-handling and rendering loop.

Understanding hangs in your app

Determine the cause for delays in user interactions by examining the main thread and the main run loop.

Understanding hitches in your app

Determine the cause of interruptions in motion by examining the render loop.

Diagnosing performance issues early

Diagnose potential performance issues in your app during testing with the Thread Performance Checker tool in Xcode.

Reducing your app’s launch time

Create a more responsive experience with your app by minimizing time spent in startup.

Reducing disk writes

Improve your app’s responsiveness by optimizing how it writes data to permanent storage.

