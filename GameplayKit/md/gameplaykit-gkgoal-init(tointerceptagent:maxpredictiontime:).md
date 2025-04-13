

- GameplayKit
- GKGoal
-  init(toInterceptAgent:maxPredictionTime:) 

Initializer

# init(toInterceptAgent:maxPredictionTime:)

Creates a goal whose effect is to make an agent pursue the specified other agent, taking into account the target’s movement.

iOS 9.0+iPadOS 9.0+Mac Catalyst 13.1+macOS 10.11+tvOS 9.0+visionOS 1.0+

``` source
convenience init(
    toInterceptAgent target: GKAgent,
    maxPredictionTime: TimeInterval
)
```

## Parameters 

`target`  

An agent whose position affected agents will attempt to move toward.

`maxPredictionTime`  

The amount of time for which to predict the target agent’s movement.

## Return Value

A new goal object.

## Discussion

The `maxPredictionTime` parameter controls how far in the future the agent will plan to intercept its target. A larger value causes an affected agent to pursue its quarry more efficently, catching up with the target’s motion using fewer course corrections. A smaller value causes an affected agent to more closely follow the target’s current position despite the target’s current speed (and depending on the properties of the affected agent, it might not be able to move quickly enough to catch its target).

## See Also

### Creating Goals for Avoidance and Interception Behavior

convenience init(toAvoid: [GKAgent], maxPredictionTime: TimeInterval)

Creates a goal whose effect is to make an agent avoid colliding with the specified other agents, taking into account the other agents’ movement.

convenience init(toAvoid: [GKObstacle], maxPredictionTime: TimeInterval)

Creates a goal whose effect is to make an agent avoid colliding with the specified static obstacles.

