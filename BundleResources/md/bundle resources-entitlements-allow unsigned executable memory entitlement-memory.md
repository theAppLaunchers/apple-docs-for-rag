

- Bundle Resources
- Entitlements
-  Allow Unsigned Executable Memory Entitlement 

Property List Key

# Allow Unsigned Executable Memory Entitlement

A Boolean value that indicates whether the app may create writable and executable memory without the restrictions imposed by using the `MAP_JIT` flag.

macOS 10.7+

## Details 

Key  
com.apple.security.cs.allow-unsigned-executable-memory

Type  

boolean

## Discussion

In rare cases, an app might need to override or patch C code, use the long-deprecated `NSCreateObjectFileImageFromMemory` (which is fundamentally insecure), or use the DVDPlayback framework. Add the Allow Unsigned Executable Memory Entitlement to enable these use cases. Otherwise, the app might crash or behave in unexpected ways.

Important

Including this entitlement exposes your app to common vulnerabilities in memory-unsafe code languages. Carefully consider whether your app needs this exception.

To add the entitlement to your app, first enable the Hardened Runtime capability in Xcode, and then under Runtime Exceptions, select Allow Unsigned Executable Memory.

## See Also

### Security

App Sandbox

Restrict access to system resources and user data in macOS apps to contain damage if an app becomes compromised.

App Sandbox Entitlement

A Boolean value that indicates whether the app may use access control technology to contain damage to the system and user data if an app is compromised.

**Key:** com.apple.security.app-sandbox

com.apple.security.network.server

A Boolean value indicating whether your app may listen for incoming network connections.

com.apple.security.network.client

A Boolean value indicating whether your app may open outgoing network connections.

Camera entitlement

A Boolean value that indicates whether the app may interact with the built-in and external cameras, and capture movies and still images.

**Key:** com.apple.security.device.camera

com.apple.security.device.microphone

A Boolean value that indicates whether the app may use the microphone.

com.apple.security.device.usb

A Boolean value indicating whether your app may interact with USB devices.

com.apple.security.print

A Boolean value indicating whether your app may print a document.

com.apple.security.device.bluetooth

A Boolean value indicating whether your app may interact with Bluetooth devices.

Address book entitlement

A Boolean value that indicates whether the app may have read-write access to contacts in the user’s address book.

**Key:** com.apple.security.personal-information.addressbook

Location entitlement

A Boolean value that indicates whether the app may access location information from Location Services.

**Key:** com.apple.security.personal-information.location

Calendars entitlement

A Boolean value that indicates whether the app may have read-write access to the user’s calendar.

**Key:** com.apple.security.personal-information.calendars

com.apple.security.files.user-selected.read-only

A Boolean value that indicates whether the app may have read-only access to files the user has selected using an Open or Save dialog.

com.apple.security.files.user-selected.read-write

A Boolean value that indicates whether the app may have read-write access to files the user has selected using an Open or Save dialog.

com.apple.security.files.downloads.read-only

A Boolean value that indicates whether the app may have read-only access to the Downloads folder.

