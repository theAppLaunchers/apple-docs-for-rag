Framework

# TelephonyMessagingKit

Send and receive standards-based messages over cellular networks.

iOS 26.0+BetaiPadOS 26.0+Beta

## [Overview](/documentation/TelephonyMessagingKit#overview)

To use TelephonyMessagingKit, use the shared instance of [`TelephonyMessagingSession`](/documentation/telephonymessagingkit/telephonymessagingsession) as your app’s main point of contact with the framework. Using a session, your app can inspect the services currently available on the device. The framework supports Short Message Service (SMS), Multimedia Messaging Service (MMS), and Rich Communication Services (RCS).

Each service provides an asynchronous sequence for notifications of incoming messages that the app can handle. To send a new message, compose the message content and then call the `send` method appropriate to the service. The RCS service, if present, provides functionality that goes beyond one-to-one messaging, including group chat and chatbots.

Note

TelephonyMessagingKit supports SMS, MMS, and RCS messaging only on iPhone devices. The framework has no functionality on iPadOS or on iOS apps running in visionOS or in macOS on Apple silicon. The framework ignores calls from Mac apps built with Mac Catalyst.

### [Default carrier messaging apps](/documentation/TelephonyMessagingKit#Default-carrier-messaging-apps)

To have access to the TelephonyMessageKit API you must add the [`Default Carrier Messaging App`](/documentation/BundleResources/Entitlements/com.apple.developer.carrier-messaging-app) entitlement to your app. This functionality will be enabled in your app only when the user selects your app to be the default carrier messaging app.

Important

You may develop and test TelephonyMessagingKit apps on devices in all regions by using an Apple-provided provisioning profile. People using your app must have an account registered in the European Union (EU), and their device must be located within the EU.

## [Topics](/documentation/TelephonyMessagingKit#topics)

### [Essentials](/documentation/TelephonyMessagingKit#Essentials)

```swift
```swift
```swift
```swift
class TelephonyMessagingSession
```
```

An object that coordinates interaction with the TelephonyMessagingKit framework.
```

[`Default Carrier Messaging App`](/documentation/BundleResources/Entitlements/com.apple.developer.carrier-messaging-app)

A Boolean value that indicates whether the app can use the TelephonyMessagingKit framework to serve as the default carrier messaging app.
```

### [Supporting types](/documentation/TelephonyMessagingKit#Supporting-types)

```swift
```swift
```swift
```swift
struct RCSFileTransferMetadata
```
```

A structure that contains metadata about an RCS file transfer.
```
```swift
```swift
```swift
struct RCSGroupContext
```
```

Structure containing information about a message’s group.
```
```

Beta Software

This documentation contains preliminary information about an API or technology in development. This information is subject to change, and software implemented according to this documentation should be tested with final operating system software.

[Learn more about using Apple's beta software](https://developer.apple.com/support/beta-software/)