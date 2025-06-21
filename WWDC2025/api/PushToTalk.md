Framework

# Push to Talk

Display the system user interface for your app’s Push to Talk services.

iOS 16.0+iPadOS 16.0+Mac Catalyst 16.0+

## [Overview](/documentation/PushToTalk#overview)

The Push to Talk framework is a power-efficient, user-friendly, and privacy-focused API. It gives your apps the ability to provide user interface controls that allow your users to transmit audio from anywhere. It supplies an ephemeral Apple Push Notification service token so the system can wake your app in the background to handle incoming audio while a session is ongoing.

Note

Push to Talk services aren’t available to compatible iPad and iPhone apps running in visionOS.

## [Topics](/documentation/PushToTalk#topics)

### [Essentials](/documentation/PushToTalk#Essentials)

[

Creating a Push to Talk app](/documentation/pushtotalk/creating-a-push-to-talk-app)

Build a walkie-talkie style app with system user interface controls.

```swift
```swift
```swift
class PTChannelManager
```
```

An object that represents a push-to-talk channel manager.
```

### [Channel management](/documentation/PushToTalk#Channel-management)

```swift
```swift
```swift
```swift
protocol PTChannelManagerDelegate
```
```

A type that represents your life cycle of a channel manager.
```
```swift
```swift
```swift
enum PTTransmissionMode
```
```

Identifies the type of audio transmission modes.
```
```swift
```swift
```swift
enum PTServiceStatus
```
```

Identifies the type that indicates the status of the service.
```
```swift
```swift
```swift
enum PTChannelJoinReason
```
```

Identifies the type that indicates the join reason.
```
```swift
```swift
```swift
enum PTChannelLeaveReason
```
```

Identifies the type that indicates the leave reason.
```
```swift
```swift
```swift
enum PTChannelTransmitRequestSource
```
```

Identifies the type that indicates the transmission request source.
```
```

### [Channel restoration](/documentation/PushToTalk#Channel-restoration)

```swift
```swift
```swift
```swift
class PTChannelDescriptor
```
```

An object that describes a channel.
```
```swift
```swift
```swift
protocol PTChannelRestorationDelegate
```
```

A type that represents the channel restoration behavior.
```
```

### [Channel participants](/documentation/PushToTalk#Channel-participants)

```swift
```swift
```swift
```swift
class PTParticipant
```
```

An object that represents a participant.
```
```

### [Push notification results](/documentation/PushToTalk#Push-notification-results)

```swift
```swift
```swift
```swift
class PTPushResult
```
```

An object that represents a push result.
```
```

### [Push to Talk errors](/documentation/PushToTalk#Push-to-Talk-errors)

```swift
```swift
```swift
```swift
struct PTChannelError
```
```

A structure that represents a channel error.
```
```swift
```swift
```swift
enum Code
```
```

Error codes for channel operations.
```
```swift
```swift
```swift
struct PTInstantiationError
```
```

A structure that represents an instantiation error.
```
```swift
```swift
```swift
enum Code
```
```

Error codes for instantiation operations.
```
```swift
```swift
```swift
let PTChannelErrorDomain: String
```
```

A string representation of the channel error domain.
```
```swift
```swift
```swift
let PTInstantiationErrorDomain: String
```
```

A string representation of the instantiation error domain.
```
```