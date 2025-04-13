

- GameKit
- GKMatchmakerViewController
-  canStartWithMinimumPlayers 

Instance Property

# canStartWithMinimumPlayers

A Boolean value that indicates whether your game can start after a minimum number of players join a match.

iOS 15.0+iPadOS 15.0+Mac Catalyst 15.0+macOS 12.0+tvOS 15.0+visionOS 1.0+

``` source
@MainActor
var canStartWithMinimumPlayers: Bool { get set }
```

## Mentioned in 

Finding multiple players for a game

## Discussion

If you set this property to true, players can optionally start a multiplayer game when the minimum number of players accept their invitations. Design your game to progressively add additional players up to the maximum number of players. The default value for this property is false.

To set the minimum and maximum number of players, see Create a match request.

## See Also

### Creating and configuring the view controller

init?(matchRequest: GKMatchRequest)

Creates a matchmaker view controller for the local player to start inviting other players.

init?(invite: GKInvite)

Creates a matchmaker view controller to present to a player who accepts an invitation.

var matchRequest: GKMatchRequest

The configuration for the desired match.

var matchmakingMode: GKMatchmakingMode

The mode that a multiplayer game uses to find players.

enum GKMatchmakingMode

Possible modes that a multiplayer game uses to find matches.

