

- Game Controller
- GCController
-  playerIndex 

Instance Property

# playerIndex

The player index for the controller.

iOS 7.0+iPadOS 7.0+Mac Catalyst 13.1+macOS 10.9+tvOS 9.0+visionOS 1.0+

``` source
var playerIndex: GCControllerPlayerIndex { get set }
```

## Discussion

Use the player index to identify which player is using the controller. Set the player index when the controller first connects to the device and you configure your game.

When you set the player index, the matching LED on the controller for that player lights up. You don’t need to provide a unique player index for each active game controller. For example, players on the same team can share a common player index. If your game no longer uses a controller, set the controller’s index value to GCControllerPlayerIndex.indexUnset.

The default value for this property is GCControllerPlayerIndex.indexUnset.

Important

In iOS 13 and later, tvOS 13 and later, and macOS 10.15 and later, two apps can use the same player index. Prior to these releases, if another app uses the index, this framework sets the player index in the other app to GCControllerPlayerIndex.indexUnset.

## See Also

### Identifying controllers and displaying a player index

enum GCControllerPlayerIndex

The possible values for controller player indices.

