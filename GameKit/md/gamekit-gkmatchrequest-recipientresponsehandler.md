

- GameKit
- GKMatchRequest
-  recipientResponseHandler 

Instance Property

# recipientResponseHandler

A method that handles when a player responds to an invitation to join a match.

iOS 8.0+iPadOS 8.0+Mac Catalyst 13.1+macOS 10.10+tvOS 9.0+visionOS 1.0+watchOS 3.0+

``` source
var recipientResponseHandler: ((GKPlayer, GKInviteRecipientResponse) -> Void)? { get set }
```

## Discussion

The block receives the following parameters:

`player`  
The player who receives the invitation.

`GKInviteeRecipientResponse`  
The player’s response to the invitation.

GameKit calls this handler once for each player who receives an invitation to join the match. You can use this handler to update your interface to show the individual player responses.

## See Also

### Inviting players

var inviteMessage: String?

The message sent to other players when the local player invites them to join a match.

var recipients: [GKPlayer]?

The players to invite to the match.

enum GKInviteRecipientResponse

A player’s response to an invitation to join a match.

