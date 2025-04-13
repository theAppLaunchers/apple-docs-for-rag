

- GameplayKit
- GKState
-  isValidNextState(\_:) 

Instance Method

# isValidNextState(\_:)

Returns a Boolean value indicating whether a state machine currently in this state is allowed to transition into the specified state.

iOS 9.0+iPadOS 9.0+Mac Catalyst 13.1+macOS 10.11+tvOS 9.0+visionOS 1.0+

``` source
func isValidNextState(_ stateClass: AnyClass) -> Bool
```

## Parameters 

`stateClass`  

A custom GKState class used in the same state machine as this state.

## Return Value

true if a transition into the specified state should be allowed; otherwise, false.

## Discussion

When you call the canEnterState(_:) or enter(_:) method of a GKStateMachine object currentState property is this state, the state machine calls this method to determine whether a transition to the proposed next state is allowed. Override this method in each custom state class you implement to choose which other states should be valid transitions from this state.

Note

GameplayKit may call this method at any time. Your implementation of this method should describe the static relationships between state classes that determine the set of edges in a state machine’s state graph. Do not use this method to conditionally control state transitions—instead, perform such conditional logic before calling a state machine’s enter(_:) method.

By restricting the set of valid state transitions, you can use a state machine to enforce invariant conditions in your code. For example, if one state class can be entered only after a state machine has passed through a series of other states, code in that state class can safely assume that any actions performed by those other states have already occurred.

## See Also

### Working with State Machines

var stateMachine: GKStateMachine?

The state machine that owns this state object.

