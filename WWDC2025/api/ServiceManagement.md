Framework

# Service Management

Manage startup items, launch agents, and launch daemons from within an app.

Mac Catalyst 13.0+macOS 10.6+

## [Overview](/documentation/ServiceManagement#overview)

Use Service Management to install and observe the permission settings of three supplemental helper executables that macOS supports. You can use all three of these to provide additional functionality related to your app, from inside your app’s bundle:

LoginItems

An app that `launchd` starts when the user logs in. A `LoginItem` is an app that continues running until the user logs out or manually quits. Its primary purpose is to enable the system to launch helper executables automatically

LaunchAgents

Processes that run on behalf of the currently logged-in user. `launchd`, a system-level process, manages Agents. Agents can communicate with other processes in the same user session and with system-wide daemons in the system context.

LaunchDaemons

A stand-alone background process that `launchd` manages on behalf of the user and which runs as root and may run before any users have logged on to the system. A daemon doesn’t interact with a user process directly; it can only respond to requests made by user processes in the form of a low-level request, such as a system request, for example [XPC](/documentation/Foundation/xpc), low-level Interprocess Communications system.

## [Topics](/documentation/ServiceManagement#topics)

### [Essentials](/documentation/ServiceManagement#Essentials)

[

Updating helper executables from earlier versions of macOS](/documentation/servicemanagement/updating-helper-executables-from-earlier-versions-of-macos)

Simplify your app’s helper executables and support new authorization controls.

[

Updating your app package installer to use the new Service Management API](/documentation/servicemanagement/updating-your-app-package-installer-to-use-the-new-service-management-api)

Learn about the Service Management API with a GUI-less agent app.

### [Management](/documentation/ServiceManagement#Management)

```swift
```swift
```swift
```swift
class SMAppService
```
```

An object the framework uses to control helper executables that live inside an app’s main bundle.
```
```swift
```swift
```swift
func SMJobBless(CFString!, CFString, AuthorizationRef!, UnsafeMutablePointer<Unmanaged<CFError>?>!) -> Bool
```
```

Submits the executable for the given label as a job to `launchd`.

Deprecated
```

[

API Reference

Authorization Constants](/documentation/servicemanagement/authorization-constants)

Constants that describe the ability to authorize helper executables or modify daemon applications.

[

API Reference

Property List Keys](/documentation/servicemanagement/property-list-keys)

Property list keys that describe the kinds of applications, daemons, and helper executables the framework manages.
```

### [Enablement](/documentation/ServiceManagement#Enablement)

```swift
```swift
```swift
```swift
func SMLoginItemSetEnabled(CFString, Bool) -> Bool
```
```

Enables a helper executable in the main app-bundle directory.

Deprecated
```
```

### [Status](/documentation/ServiceManagement#Status)

```swift
```swift
```swift
```swift
enum Status
```
```

Constants that describe the registration or authorization status of a helper executable.
```
```

### [Errors](/documentation/ServiceManagement#Errors)

[

API Reference

Service Management Errors](/documentation/servicemanagement/service-management-errors)

Errors that the framework returns.

### [Deprecated](/documentation/ServiceManagement#Deprecated)

[

API Reference

Deprecated Symbols](/documentation/servicemanagement/deprecated-symbols)

### [Variables](/documentation/ServiceManagement#Variables)

```swift
```swift
```swift
```swift
let SMAppServiceErrorDomain: String
```
```
```
```