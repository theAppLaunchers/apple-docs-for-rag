

- GameplayKit
- GKState
-  didEnter(from:) 

Instance Method

# didEnter(from:)

Performs custom actions when a state machine transitions into this state.

iOS 9.0+iPadOS 9.0+Mac Catalyst 13.1+macOS 10.11+tvOS 9.0+visionOS 1.0+

``` source
func didEnter(from previousState: GKState?)
```

## Parameters 

`previousState`  

The state the state machine transitioned from to enter this state. If the current state is the initial state of the state machine, this parameter’s value is `nil`.

## Discussion

Override this method when the actions you want to perform in response to a state change should be associated with the new state, or when those actions depend on which state a state machine was previously in.

For example, in a game where each enemy character has Chase, Flee, Dead, and Respawn states, it might make sense to change the character’s visual appearance when in each state. By putting the appearance-changing code in each state, you ensure that the appearance that corresponds to each state is used only when entering that state.

Or, in a state machine that governs a game’s user interface, with Menu, Playing, Paused, and GameOver states, the visual effects for starting a game might differ depending on whether one enters the game from the main menu or restarts from a Game Over screen.

## See Also

### Handling State Transitions and Updates

func update(deltaTime: TimeInterval)

Performs custom actions when a state machine updates while in this state.

func willExit(to: GKState)

Performs custom actions when a state machine transitions out of this state.

