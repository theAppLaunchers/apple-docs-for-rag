

- GameKit
- GKMatchmakerViewController
-  setHostedPlayer(\_:didConnect:) 

Instance Method

# setHostedPlayer(\_:didConnect:)

Updates the connection status of a player in a hosted game.

iOS 8.0+iPadOS 8.0+Mac Catalyst 13.1+macOS 10.10+tvOS 9.0+visionOS 1.0+

``` source
@MainActor
func setHostedPlayer(
    _ player: GKPlayer,
    didConnect connected: Bool
)
```

## Parameters 

`player`  

The player whose status changed.

`connected`  

A Boolean value that indicates whether the player connected or disconnected from the hosted match.

## Discussion

When you connect or disconnect a player from your server in a hosted game, use this method to update the player’s status that appears in the matchmaker view controllers on other player’s devices. For example, invoke this method after you connect a player from the matchmakerViewController(_:hostedPlayerDidAccept:) delegate method.

## See Also

### Hosting matches

var isHosted: Bool

A Boolean value that indicates whether the match is hosted or peer-to-peer.

