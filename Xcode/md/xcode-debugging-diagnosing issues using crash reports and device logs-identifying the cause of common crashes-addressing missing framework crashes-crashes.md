

- Xcode
- Debugging
- Diagnosing issues using crash reports and device logs
- Identifying the cause of common crashes
-  Addressing missing framework crashes 

Article

# Addressing missing framework crashes

Identify missing frameworks from a crash report, and adjust your app’s build to correctly include the framework.

## Overview

If you modularize your app’s functionality into frameworks, the app must link the frameworks at build time, and also embed a copy of the frameworks inside the app bundle during the build. If an app links a framework but doesn’t embed it, the app crashes at launch, because the dynamic linker can’t locate the missing framework.

### Identify the missing framework

The dynamic linker, `dyld`, outputs detailed information about the framework it couldn’t locate, in the `Termination Description` of the crash report:

```
Exception Type: EXC_CRASH (SIGABRT)
Exception Codes: 0x0000000000000000, 0x0000000000000000
Exception Note: EXC_CORPSE_NOTIFY
Termination Description: DYLD, 
    dependent dylib '@rpath/MyFramework.framework/MyFramework' not found for '/MyCoolApp.app/MyCoolApp',
    tried but didn't find: 
    '/usr/lib/swift/MyFramework.framework/MyFramework' 
    '/MyCoolApp.app/Frameworks/MyFramework.framework/MyFramework' 
    '@rpath/MyFramework.framework/MyFramework' 
    '/System/Library/Frameworks/MyFramework.framework/MyFramework'
```

The exact message depends on the operating system and operating system version. Here’s a different example:

```
Exception Type: EXC_CRASH (SIGABRT)
Exception Codes: 0x0000000000000000, 0x0000000000000000
Exception Note: EXC_CORPSE_NOTIFY
Termination Description: DYLD, Library not loaded: @rpath/MyFramework.framework/MyFramework 
    | Referenced from: /MyCoolApp.app/MyCoolApp 
    | Reason: image not found
```

Note

For readability, extra line breaks are in this example. In the original crash report file for these examples, the `dyld` information is on fewer lines.

### Inspect the framework’s configuration

Ensure the framework is correctly embedded in the app bundle—see Embedding Frameworks In An App.

If you can’t reproduce the crash, archive the app, export it for Development distribution, and apply app thinning, as described in Distributing your app for beta testing and releases. Test the different variants produced through app thinning to see if the framework is missing only after applying app thinning. If this reproduces the crash, do the following:

- Verify the framework’s build setting for Architectures (`ARCHS`) is the default value.

- Verify the framework’s build setting for Valid Architectures (`VALID_ARCHS`) is the default value.

- Verify the UIRequiredDeviceCapabilities key in the framework’s `Info.plist` file correctly specifies the CPU architectures the framework supports.

Note

If the missing framework is from a third-party framework vendor or uses third-party development tools to integrate it in your app, contact the vendor for assistance in addressing the issue.

## See Also

### Related Documentation

Analyzing a crash report

Identify clues in a crash report that help you diagnose problems.

