Framework

# MailKit

Secure, customize, and act on email messages that users send and receive.

macOS 12.0+

## [Overview](/documentation/MailKit#overview)

MailKit lets your app include an app extension that customizes several features of Mail. A Mail app extension provides one or more of the following enhancements:

*   A _content blocker_ defines rules to prevent loading content when users view messages.
    
*   An _action handler_ performs actions such as flagging, setting colors, or archiving when Mail downloads messages.
    
*   A _compose session handler_ validates recipient email addresses, displays a view controller on Mail’s compose windows, confirms if messages are suitable for delivery, and adds custom headers.
    
*   A _message security handler_ secures messages using encryption and digital signatures.
    

The entry point for your extension is an object that conforms to [`MEExtension`](/documentation/mailkit/meextension). When MailKit invokes your extension, this objects determines the handlers that provide each capability in the list above.

## [Topics](/documentation/MailKit#topics)

### [Essentials](/documentation/MailKit#Essentials)

```swift
```swift
```swift
```swift
protocol MEExtension
```
```

A type that provides objects for manipulating email messages, such as performing actions on messages or blocking content when users view messages.
```

[

Build Mail App Extensions](/documentation/mailkit/build-mail-app-extensions)

Create app extensions that block content, perform message and composing actions, and help message security.
```

### [Content Blockers](/documentation/MailKit#Content-Blockers)

```swift
```swift
```swift
```swift
protocol MEContentBlocker
```
```

An object that provides a set of rules to block content when displaying a message.
```
```

### [Message Actions](/documentation/MailKit#Message-Actions)

```swift
```swift
```swift
```swift
protocol MEMessageActionHandler
```
```

An object that performs actions on messages as the system downloads them.
```
```

### [Compose Window Enhancements](/documentation/MailKit#Compose-Window-Enhancements)

```swift
```swift
```swift
```swift
protocol MEComposeSessionHandler
```
```

An object that participates in the composition of mail messages, and annotates recipient tokens.
```
```

### [Message Encryption, Decryption, and Digital Signatures](/documentation/MailKit#Message-Encryption-Decryption-and-Digital-Signatures)

```swift
```swift
```swift
```swift
protocol MEMessageSecurityHandler
```
```

An object that digitally signs or encrypts messages the user sends and receives.
```
```

### [Message Properties](/documentation/MailKit#Message-Properties)

```swift
```swift
```swift
```swift
class MEMessage
```
```

An object that contains information about a mail message, such as the subject, addressees, date sent, and the message contents.
```
```swift
```swift
```swift
enum MEMessageState
```
```

The state of a message: sent, unsent, or received.
```
```

### [Custom View Controllers](/documentation/MailKit#Custom-View-Controllers)

```swift
```swift
```swift
```swift
class MEExtensionViewController
```
```

An object that manages a view for compose session and message security handlers.
```
```

### [Structures](/documentation/MailKit#Structures)

```swift
```swift
```swift
```swift
struct MEMessageSecurityError
```
```
```
```

### [Classes](/documentation/MailKit#Classes)

```swift
```swift
```swift
```swift
class MEComposeContext
```
```
```
```swift
```swift
```swift
class MEDecodedMessageBanner
```
```
```
```swift
```swift
```swift
class MEEmailAddress
```
```
```
```swift
```swift
```swift
class MEExtensionManager
```
```
```
```

### [Reference](/documentation/MailKit#Reference)

[

API Reference

MailKit Enumerations](/documentation/mailkit/mailkit-enumerations)

[

API Reference

MailKit Constants](/documentation/mailkit/mailkit-constants)