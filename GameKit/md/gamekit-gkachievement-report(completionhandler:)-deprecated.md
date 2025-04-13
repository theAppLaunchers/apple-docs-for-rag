

- GameKit
- GKAchievement
-  report(completionHandler:) Deprecated

Instance Method

# report(completionHandler:)

Reports the player’s progress to Game Center.

macOS 10.8–10.10DeprecatedvisionOS 1.0–1.0DeprecatedwatchOS 2.0–2.0Deprecated

**macOS, visionOS, watchOS**

``` source
func report(completionHandler: (((any Error)?) -> Void)? = nil)
```

**visionOS**

``` source
func report() async throws
```

## Parameters 

`completionHandler`  

A block to be called after the operation completes.

The block takes the following parameter:

*error*  
If the operation was successful, this value is `nil`; otherwise, this parameter holds an object that describes the problem that occurred.

## Discussion

When the player makes progress towards completing an achievement, your game communicates the player’s progress to Game Center by calling this method. An achievement object is implicitly tied to the local player that was authenticated when the object was created; your game should only report progress when the same local player is still authenticated on the device.

Note

To avoid using network bandwidth unnecessarily, only report an achievement when the player has made more progress towards completing it.

When the progress is successfully reported, the achievement is made visible if it was previously hidden. The percentComplete and lastReportedDate property values stored on Game Center are updated if the new percentComplete value is greater than the value previously stored on Game Center. if the value of the percentComplete property was equal to `100.0`, then the achievement is marked as completed and a banner may be shown to the player.

When this method is called, it creates a new background task to handle the request. The method then returns control to your game. The background task automatically handles network errors, resending the data until the task completes. When the task is complete, Game Kit calls your completion handler. The completion handler is always called on the main thread.

## See Also

### Related Documentation

var showsCompletionBanner: Bool

A Boolean value that indicates whether GameKit displays a banner when the player completes the achievement.

var isHidden: Bool

A Boolean value that indicates whether the system hides this achievement from the player.

Deprecated

var isCompleted: Bool

A Boolean value that states whether the player has completed the achievement.

### Deprecated Methods

func issueChallenge(toPlayers: [String]?, message: String?)

Issues an achievement challenge to a list of players.

Deprecated

func selectChallengeablePlayerIDs([String]?, withCompletionHandler: (([String]?, (any Error)?) -> Void)?)

Finds the subset of players who can earn an achievement.

Deprecated

