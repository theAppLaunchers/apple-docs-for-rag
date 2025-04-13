

- MailKit
- MEComposeSessionHandler
-  allowMessageSendForSession(\_:completion:) 

Instance Method

# allowMessageSendForSession(\_:completion:)

Confirms that the message is ready for delivery.

macOS 12.0+

``` source
@MainActor
optional func allowMessageSendForSession(
    _ session: MEComposeSession,
    completion: @escaping ((any Error)?) -> Void
)
```

``` source
@MainActor
optional func allowMessageSendForSession(_ session: MEComposeSession) async throws
```

## Parameters 

`session`  

The session that represents the properties of the message in the compose window.

`completion`  

A block you call after determining if the message is ready for delivery.

## Discussion

Important

You can call this method from synchronous code using a completion handler, as shown on this page, or you can call it as an asynchronous method that has the following declaration:

```
optional func allowMessageSendForSession(_ session: MEComposeSession) async throws
```

For information about concurrency and asynchronous code in Swift, see Calling Objective-C APIs Asynchronously.

MailKit gives your compose session handler an opportunity to confirm that a message is ready for delivery. If the message is ready for delivery and needs no further attention, call the completion handler and pass `nil`.

If there’s an issue with the message’s content and you want to prompt the user, call the completion handler and pass an error that contains a localized description of the reason the message isn’t ready. For example, the following code calls the completion handler with an error if a recipient uses the domain `@example.com`.

```
enum ComposeSessionError: LocalizedError {
    case invalidRecipientDomain

    var errorDescription: String? {
        switch self {
        case .invalidRecipientDomain:
            return "example.com is not a valid recipient domain"
        }
    }
}

func allowMessageSendForSession(_ session: MEComposeSession, completion: @escaping (Error?) -> Void) {
    // Confirm none of the recipients use @example.com.
    if session.mailMessage.allRecipientAddresses.contains(where: { $0.hasSuffix("@example.com")}) {
        completion(ComposeSessionError.invalidRecipientDomain)
    } else {
        completion(nil)
    }
}
```

Note

The alert that the system displays to the user is advisory only. The user can choose to send the message regardless of the issue your compose session handler indicates.

