

- GameplayKit
- GKCompositeBehavior
-  weight(for:) 

Instance Method

# weight(for:)

Returns the weight for the specified individual behavior’s influence on agents.

iOS 9.0+iPadOS 9.0+Mac Catalyst 13.0+macOS 10.11+tvOS 9.0+visionOS 1.0+

``` source
func weight(for behavior: GKBehavior) -> Float
```

## Parameters 

`behavior`  

An individual behavior already included in the composite behavior.

## Return Value

The weight applied to that behavior’s influence on an agent’s speed and direction, or `0.0` if that behavior is not in the composite behavior.

## Discussion

When an agent evaluates a composite behavior, it examines all goals across all of the individual behaviors it contains. For each goal, the agent calculates the change in direction and speed necessary to move toward fulfilling that goal (within the limits of the current time step and the agent’s maximum speed and turn rate). The agent then combines these influences to determine the total change in direction and speed for the current time step.

Weights modulate the effects of multiple goals in a behavior. Individual goals, or individual behaviors that group goals in a composite behavior, have more influence on an agent when given a greater weight.

## See Also

### Related Documentation

subscript(GKBehavior) -> NSNumber

Returns the weight associated with the behavior specified by subscript syntax.

subscript(Int) -> GKBehavior

Returns the individual behavior at the specified index in the composite behavior’s list of behaviors.

### Managing the Individual Behaviors in a Composite Behavior

func setWeight(Float, for: GKBehavior)

Sets the weight for the specified individual behavior’s influence on agents, adding that behavior to the composite behavior if it is not already present.

func remove(GKBehavior)

Removes the specified individual behavior from the composite behavior.

func removeAllBehaviors()

Removes all individual behaviors from the composite behavior.

var behaviorCount: Int

The number of individual behaviors in the composite behavior.

