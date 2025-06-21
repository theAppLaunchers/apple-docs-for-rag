Framework

# PermissionKit

Create communication experiences between a child and their parent or guardian.

iOS 26.0+BetaiPadOS 26.0+BetaMac Catalyst 26.0+BetamacOS 26.0+BetavisionOS 26.0+Beta

## [Overview](/documentation/PermissionKit#Overview)

Use `PermissionKit` in your app to adjust communication rules for a child account on iCloud. `PermissionKit` provides a way to create consistent asking experiences between a child and their parent or guardian that maintains UI consistency with other communication experiences across the system.

Important

Communication experiences using the `PermissionKit` framework are only available using iMessage.

## [Topics](/documentation/PermissionKit#topics)

### [Essentials](/documentation/PermissionKit#Essentials)

[

Creating a communication experience](/documentation/permissionkit/creating-a-communication-experience)

Request permission from a parent or guardian to modify a child’s communication rules.

### [Permission buttons](/documentation/PermissionKit#Permission-buttons)

```swift
```swift
```swift
```swift
struct CommunicationLimitsButton
```
```

A button that presents a system UI to a parent or guardian to ask for an exception to a child’s communication limits.
```
```

### [Permission responses](/documentation/PermissionKit#Permission-responses)

```swift
```swift
```swift
```swift
class CommunicationLimits
```
```

A type that encapsulates the communication limits for your app.
```
```swift
```swift
```swift
struct CommunicationHandle
```
```

A piece of identifying information that can be used to communicate with someone.
```
```swift
```swift
```swift
struct PermissionResponse
```
```

A full permission response that includes the original question and chosen answer.
```
```

### [Permission questions](/documentation/PermissionKit#Permission-questions)

```swift
```swift
```swift
```swift
protocol QuestionTopic
```
```

A protocol that defines a question topic that can be used to interpret what a user is asking for.
```
```swift
```swift
```swift
class PermissionQuestion
```
```

A class that captures a permission question posed by a user.
```
```swift
```swift
```swift
struct CommunicationTopic
```
```

A question topic related to communication.
```
```swift
```swift
```swift
struct PermissionChoice
```
```

A class that uniquely identifies a specific, statically defined permission choice.
```
```

### [Error response](/documentation/PermissionKit#Error-response)

```swift
```swift
```swift
```swift
enum AskError
```
```

An error that can occur when asking someone to send a communication permission question.
```
```

Beta Software

This documentation contains preliminary information about an API or technology in development. This information is subject to change, and software implemented according to this documentation should be tested with final operating system software.

[Learn more about using Apple's beta software](https://developer.apple.com/support/beta-software/)