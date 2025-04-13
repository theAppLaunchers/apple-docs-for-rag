

- XCUIAutomation
- XCUIApplication
-  init(bundleIdentifier:) 

Initializer

# init(bundleIdentifier:)

Creates a proxy for an application for the specified bundle identifier.

iOSiPadOSMac CatalystmacOStvOSvisionOSwatchOSXcode 16.3+

``` source
@MainActor
init(bundleIdentifier: String)
```

## Discussion

Use this initializer to launch an application based on its bundle identifier. For more information about bundle identifiers, see About Bundle IDs in the App Distribution Guide.

Although every app has a unique bundle ID, there are times when XCUIAutomation needs to decide which particular build of an app to use for testing. With macOS, multiple builds of the same app can exist on a single device. With iOS and tvOS, a build of the app may need to be copied onto the device for testing. In both cases, XCUIAutomation detects a matching build to use in the following order, based on the current test scheme selected in Xcode:

1.  Any matching build in the Target Dependencies list of a test target built by the test scheme

2.  Any matching build from the Targets list of the test scheme’s Build action

3.  Any matching build from the root level of the test target’s Build Products folder

For iOS and tvOS apps, the system installs the matching app build onto the device and launches it. If the system can’t find the matching app build, it launches the existing installed app for the requested bundle ID.

For macOS apps, the system launches the matching app build from its existing location. If the system can’t find the matching app build, it launches the default app build on the device for the requested bundle ID (as determined by Launch Services).

## See Also

### Creating an application proxy

init()

Creates a proxy for the application that’s configured as the Target Application in Xcode’s target settings.

init(url: URL)

Creates a proxy for the application at the specified file system URL.

