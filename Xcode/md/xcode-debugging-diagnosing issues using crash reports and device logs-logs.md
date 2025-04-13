

- Xcode
- Debugging
-  Diagnosing issues using crash reports and device logs 

# Diagnosing issues using crash reports and device logs

Use crash reports and device logs to debug app issues.

## Overview

Customers expect apps to be stable, free of bugs, and use system resources efficiently. The operating system helps you meet these expectations by collecting different log types you can use to diagnose issues in your app:

- Crash reports describe how your app terminated, and document the code running on each thread at the time of the crash.

- Jetsam event reports describe the system-memory conditions under which the operating system terminated an app.

- Device console logs contain detailed information on operations that occur in both the operating system and apps.

Distribution builds of your app, such as for the App Store, an enterprise environment, or a testing team, require you to use crash reports and device logs to diagnose issues encountered by your customers. Distribution builds don’t contain the necessary entitlements for debugging in Xcode.

### Address stability issues using crash reports

Crash reports are the most common type of log you’ll use when diagnosing an issue. When receiving crash reports for your app, use them to understand the stability problems the app is having. A crash report describes how your app terminated, and also contains the complete backtrace of each thread, which shows the code running at the time of the crash.

To debug a problem using a crash report:

1.  Build your app with symbol information and retain the Xcode archive before distributing the app.

2.  Retrieve a crash report for an issue. See Acquiring crash reports and diagnostic logs for the different ways you can retrieve crash reports.

3.  Convert the hexadecimal addresses into symbol names for your app, as described in Adding identifiable symbol names to a crash report.

4.  Determine if the crash fits any of the patterns in Identifying the cause of common crashes. Consult Analyzing a crash report and Examining the fields in a crash report for additional insight on the issue.

5.  Update your code to fix the issue.

6.  Add tests with the XCTest framework to ensure the issue doesn’t reoccur in the future.

### Uncover memory inefficiencies using jetsam event reports

Ensure that your apps use memory efficiently. When an app on iOS, iPadOS, tvOS, visionOS, or watchOS uses memory inefficiently, less memory is available for other apps to remain in memory in the background. This lower available memory limits how quickly a user can switch between apps, because apps can’t resume from memory and must first complete a full app launch.

When the operating system experiences low-memory conditions, and requires more memory than is currently free, the device’s operating system can terminate apps to reclaim the memory they’re using. A jetsam event report describes the system-memory conditions under which the operating system terminated an app. See Locate crash reports and memory logs on the device for how to access these logs and Identifying high-memory use with jetsam event reports for information on intrepreting a jetsam event report.

Jetsam event reports don’t contain stack traces of executing threads in an app, but they do contain additional system information about memory use. When your app crashes due to memory pressure, see Gathering information about memory use to understand your app’s memory use patterns, and Responding to low-memory warnings to learn when to lower your memory use.

### Diagnose problems using device console logs

Apple devices maintain a continuous in-memory transcript of operations in the operating system and individual apps. These logs can be reviewed after an issue occurs. Some issues, such as problems installing an app, can be diagnosed by reviewing the operating system logs using the Console app on macOS. See Access device console logs for instructions on accessing a device’s console log.

Add log messages for your app to the operating system’s log with the Logging framework. The logs you provide can contain additional grouping and labeling information to assist with tracing an issue from the original user action. This information is useful for diagnosing complex interactions, such as debugging the interaction between your app and one of its app extensions.

Important

Don’t include privacy-sensitive information in your logs.

## Topics

### Essentials

Acquiring crash reports and diagnostic logs

Gather crash reports and device logs from the App Store, TestFlight, and directly from devices.

### Crash reports

Adding identifiable symbol names to a crash report

Replace hexadecimal addresses in a crash report with function names and line numbers that correspond to your app’s code.

Identifying the cause of common crashes

Find patterns in crash reports that identify common problems, and investigate the issue based on the pattern.

Analyzing a crash report

Identify clues in a crash report that help you diagnose problems.

Examining the fields in a crash report

Understand the structure of a crash report and the information each field contains.

Interpreting the JSON format of a crash report

Understand the structure and properties of the objects the system includes in the JSON of a crash report.

Understanding the exception types in a crash report

Learn what the exception type tells you about why your app crashed.

### Device logs

Identifying high-memory use with jetsam event reports

Discover why the operating system terminated your app when available memory was low.

Logging

Capture telemetry from your app for debugging and performance analysis using the unified logging system.

## See Also

### Reports

Building your app to include debugging information

Configure Xcode to produce the symbol information for debugging and crash reports.

