

- GameKit
- GKTurnBasedMatch
-  loadMatches(completionHandler:) 

Type Method

# loadMatches(completionHandler:)

Fetches the turn-based matches from Game Center that the local player participates in.

iOS 5.0+iPadOS 5.0+Mac Catalyst 13.1+macOS 10.8+tvOS 9.0+visionOS 1.0+watchOS 3.0+

``` source
class func loadMatches(completionHandler: (([GKTurnBasedMatch]?, (any Error)?) -> Void)? = nil)
```

``` source
class func loadMatches() async throws -> [GKTurnBasedMatch]
```

## Parameters 

`completionHandler`  

The block that GameKit calls when it completes the request.

The block receives the following parameters:

*matches*  
The local player’s matches, or `nil` if there are none. If an error occurs, this parameter may be non-`nil`, containing a subset of the matches that GameKit loads before the error occurs.

*error*  
Describes an error if it occurs, or `nil` if the operation completes.

## Mentioned in 

Starting turn-based matches and passing turns between players

## Discussion

The matchData properties of the match objects are `nil` until you fetch the data from Game Center using the loadMatchData(completionHandler:) method.

## See Also

### Loading Existing Matches

class func load(withID: String, withCompletionHandler: ((GKTurnBasedMatch?, (any Error)?) -> Void)?)

Loads a specific match with the specified identifier.

