

- Xcode
- Debugging
-  Building your app to include debugging information 

Article

# Building your app to include debugging information

Configure Xcode to produce the symbol information for debugging and crash reports.

## Overview

When Xcode compiles your source code into machine code, it generates a list of symbols in your app — class names, global variables, and method and function names. These symbols correspond to the file and line numbers where they’re defined; this association creates a *debug symbol*, so you can use the debugger in Xcode, or refer to line numbers reported by a crash report. Debug builds of an app place the debug symbols inside the compiled binary file by default, while release builds of an app place the debug symbols in a companion debug symbol (`dSYM`) file to reduce the size of the distributed app.

Each binary file in an app — the main app executable, frameworks, and app extensions — has its own `dSYM` file. The compiled binary and its companion `dSYM` file are tied together by a build UUID that’s recorded by both the built binary and `dSYM` file. If you build two binaries from the same source code but with different Xcode versions or build settings, the build UUIDs for the two binaries won’t match. A binary and a `dSYM` file are only compatible with each other when they have identical build UUIDs. Keep the `dSYM` files for the specific builds you distribute, and use them when diagnosing issues from crash reports.

### Build your app with symbol information

Before building your app for distribution, verify that the Debug Information Format build setting is set to DWARF with dSYM File. This generates the necessary `dSYM` files, so you can diagnose crashes after releasing your app. For instructions on configuring the build settings for your project, see Configuring the build settings of a target.

These `dSYM` files are the most common type of symbol file you need when debugging an app after releasing it.

### Publish your app with symbol information

When archiving your app for distribution, Xcode gathers all binaries and `dSYM` files for your app and stores them inside the Xcode archive.

If you distribute your app through the App Store or conduct a beta test using TestFlight, you have the option to include the symbol files when uploading your app to App Store Connect. You need to upload symbols with your build so the App Store can add the symbol names for your app to the crash reports, before delivering them to the Crashes organizer in Xcode. If you don’t include symbols with the upload to the App Store, you still receive the crash reports through the Crashes organizer, but without the symbol names. Xcode adds symbol names to these crash reports if the correct `dSYM` files are available on the Mac. See Diagnosing issues using crash reports and device logs for how to work with crash reports using `dSYM` files.

Important

You must retain the Xcode archive for each build of your app you distribute. Without this archive, you might not be able to diagnose an issue from crash reports.

For more information on archiving your app for distribution, see Distributing your app for beta testing and releases.

## See Also

### Reports

Diagnosing issues using crash reports and device logs

Use crash reports and device logs to debug app issues.

