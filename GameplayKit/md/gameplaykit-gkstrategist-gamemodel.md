

- GameplayKit
- GKStrategist
-  gameModel 

Instance Property

# gameModel

The model representing the current state of the game.

iOS 9.0+iPadOS 9.0+Mac Catalyst 13.0+macOS 10.11+tvOS 9.0+visionOS 1.0+

``` source
var gameModel: (any GKGameModel)? { get set }
```

**Required**

## Discussion

A game model—an instance of one of your custom classes implementing the GKGameModel protocol—contains all the information necessary to describe a distinct state of your game. For example, the game model class for a Tic-Tac-Toe game would encode the locations of X and O marks currently on the board and which player’s turn is next. The strategist works from the current game model when planning moves.

For more information, see GameplayKit Programming Guide.

