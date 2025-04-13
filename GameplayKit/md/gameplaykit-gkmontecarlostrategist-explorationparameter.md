

- GameplayKit
- GKMonteCarloStrategist
-  explorationParameter 

Instance Property

# explorationParameter

A value that influences whether the strategist searches more broadly or more deeply for winning game model states.

iOS 10.0+iPadOS 10.0+Mac Catalyst 13.1+macOS 10.12+tvOS 10.0+visionOS 1.0+

``` source
var explorationParameter: Int { get set }
```

## Discussion

When you call the bestMoveForActivePlayer() method, the Monte Carlo strategist performs an iterative process of randomly choosing moves, searching for a sequence of moves that ends in a win for the current player. At each step in this process, the strategist chooses whether to try a different move or to continue examining the current sequence of moves.

Higher values favor *exploration—that is,* the strategist becomes more likely to try different moves on each turn. Lower values favor *exploitation—that is,* the strategist becomes more likely to follow a sequence of moves to a possible endgame. The default value of 4 tends to balance exploration and exploitation. For best results, experiment with different values to find one that provides a style and difficulty of gameplay you prefer for your game.

## See Also

### Configuring a Strategist

var budget: Int

The maximum number of game model states the strategist will examine when searching for a move.

