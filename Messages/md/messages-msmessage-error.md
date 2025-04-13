

- Messages
- MSMessage
-  error 

Instance Property

# error

An error object describing why the system failed to send the message.

iOS 10.0+iPadOS 10.0+Mac Catalyst 13.1+

``` source
var error: (any Error)? { get set }
```

## Discussion

The system sets the `error` property when an error occurs while sending this message. It is set to `nil` if you have not yet sent the message or if you have sent the message successfully.

## See Also

### Message Properties

var accessibilityLabel: String?

A localized string that describes the message.

var isPending: Bool

A Boolean value that indicates whether the message is pending or whether it has been sent or received.

var layout: MSMessageLayout?

A layout object that defines the message’s appearance.

var senderParticipantIdentifier: UUID

A UUID identifying the participant that sent the message.

var session: MSSession?

The session that this message belongs to.

var shouldExpire: Bool

A Boolean value that determines whether the message should expire after being read.

var summaryText: String?

A succinct description of the message.

var url: URL?

A URL that encodes data to be transmitted with the message.

