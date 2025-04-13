

- GameKit
- GKMatchmaker
-  queryPlayerGroupActivity(\_:withCompletionHandler:) 

Instance Method

# queryPlayerGroupActivity(\_:withCompletionHandler:)

Finds the number of players in a player group who recently requested a match.

iOS 4.1+iPadOS 4.1+Mac Catalyst 13.1+macOS 10.8+tvOS 9.0+visionOS 1.0+

``` source
func queryPlayerGroupActivity(
    _ playerGroup: Int,
    withCompletionHandler completionHandler: ((Int, (any Error)?) -> Void)? = nil
)
```

``` source
func queryPlayerGroupActivity(_ playerGroup: Int) async throws -> Int
```

## Parameters 

`playerGroup`  

A number that uniquely identifies a subset of players in your game.

`completionHandler`  

The block that GameKit calls when it completes the request.

This block receives the following parameters:

`activity`  
The number of match requests for the player group during the previous 60 seconds.

`error`  
Describes an error if it occurs, or `nil` if the operation completes.

## Discussion

Use this method to update your interface. For example, show players the relative activity in each player group. If one group is less active than others, you might display a warning so players are aware that finding a match in that group may take longer.

## See Also

### Finding players who request matches

func queryActivity(completionHandler: ((Int, (any Error)?) -> Void)?)

Finds the number of players, across player groups, who recently requested a match.

func queryQueueActivity(String, withCompletionHandler: ((Int, (any Error)?) -> Void)?)

Finds the number of players in a specific queue who recently requested a match.

