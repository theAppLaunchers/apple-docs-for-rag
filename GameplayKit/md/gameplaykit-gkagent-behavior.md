

- GameplayKit
- GKAgent
-  behavior 

Instance Property

# behavior

A weighted collection of goals that influence the agent’s movement.

iOS 9.0+iPadOS 9.0+Mac Catalyst 13.1+macOS 10.11+tvOS 9.0+visionOS 1.0+

``` source
var behavior: GKBehavior? { get set }
```

## Discussion

When an agent evaluates its behavior, it examines each goal and calculates the change in direction and speed necessary to move toward fulfilling that goal (within the limits of the current time step and the agent’s maximum speed and turn rate). The agent then combines these influences to determine the total change in direction and speed for the current time step. You can modulate the effects of multiple goals in a behavior—use methods of this GKBehavior object to increase or decrease the relative influence of each.

For more information, see GameplayKit Programming Guide.

