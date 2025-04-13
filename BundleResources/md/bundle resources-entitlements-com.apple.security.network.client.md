

- Bundle Resources
- Entitlements
-  com.apple.security.network.client 

Property List Key

# com.apple.security.network.client

A Boolean value indicating whether your app may open outgoing network connections.

macOS 10.7+

## Details 

Type  

boolean

## Discussion

Use this key to allow your sandboxed app to connect to a server process running on another machine, or on the same machine.

Note

For TCP sockets, the `com.apple.security.network.client` and com.apple.security.network.server entitlements restrict only the initiation of a network connection, not the flow of data. Outgoing and incoming connections can both send and receive data.

For UDP sockets, the network entitlements restrict both initiation and data flow. For example, an app with only the client entitlement enabled can send, but not receive, data. Apps using UDP usually require both entitlements.

To add this entitlement to your app, enable the App Sandbox capability in Xcode, and under Network, select Outgoing Connections (Client).

## See Also

### Security

App Sandbox

Restrict access to system resources and user data in macOS apps to contain damage if an app becomes compromised.

App Sandbox Entitlement

A Boolean value that indicates whether the app may use access control technology to contain damage to the system and user data if an app is compromised.

**Key:** com.apple.security.app-sandbox

com.apple.security.network.server

A Boolean value indicating whether your app may listen for incoming network connections.

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

com.apple.security.files.downloads.read-write

A Boolean value that indicates whether the app may have read-write access to the Downloads folder.

