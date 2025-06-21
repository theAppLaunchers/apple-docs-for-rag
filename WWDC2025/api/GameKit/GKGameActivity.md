*   [GameKit](/documentation/gamekit)
*   GKGameActivity Beta

Class

# GKGameActivity

An object that represents a single instance of a game activity for the current game.

iOS 26.0+BetaiPadOS 26.0+BetaMac Catalyst 26.0+BetamacOS 26.0+BetatvOS 26.0+BetavisionOS 26.0+Beta

```swift
```swift
```swift
```swift
```swift
```swift
```swift
```swift
class GKGameActivity
```
```
```
```
```
```
```
```

## [Mentioned in](/documentation/GameKit/GKGameActivity#mentions)

[

Creating activities for your game](/documentation/gamekit/creating-activities-for-your-game)

## [Topics](/documentation/GameKit/GKGameActivity#topics)

### [Creating an activity](/documentation/GameKit/GKGameActivity#Creating-an-activity)

[`init(definition: GKGameActivityDefinition)`](/documentation/gamekit/gkgameactivity/init\(definition:\))

Initializes a game activity with definition.

```swift
```swift
```swift
class func start(definition: GKGameActivityDefinition) throws -> GKGameActivity
```
```

Initializes and starts a game activity with definition.
```
```swift
```swift
```swift
class func start(definition: GKGameActivityDefinition, partyCode: String) throws -> GKGameActivity
```
```

Creates and starts a new game activity with a custom party code.
```

### [Getting the activity definition](/documentation/GameKit/GKGameActivity#Getting-the-activity-definition)

```swift
```swift
```swift
```swift
var activityDefinition: GKGameActivityDefinition
```
```

The activity definition that this activity instance is based on.
```
```

### [Getting the activity state](/documentation/GameKit/GKGameActivity#Getting-the-activity-state)

```swift
```swift
```swift
```swift
var state: GKGameActivity.State
```
```

The state of the game activity.
```
```swift
```swift
```swift
enum State
```
```
```
```

### [Updating the activity state](/documentation/GameKit/GKGameActivity#Updating-the-activity-state)

```swift
```swift
```swift
```swift
func start()
```
```

Starts the game activity if it is not already started.
```
```swift
```swift
```swift
func pause()
```
```

Pauses the game activity if it is not already paused.
```
```swift
```swift
```swift
func resume()
```
```

Resumes the game activity if it was paused.
```
```swift
```swift
```swift
func end()
```
```

Ends the game activity if it is not already ended.
```
```

### [Getting and removing achievements](/documentation/GameKit/GKGameActivity#Getting-and-removing-achievements)

```swift
```swift
```swift
```swift
var achievements: Set<GKAchievement>
```
```

All achievements that have been associated with this activity.
```
```swift
```swift
```swift
func removeAchievements([GKAchievement])
```
```

Removes all achievements if exist.
```
```swift
```swift
```swift
func progress(on: GKAchievement) -> Double
```
```

Get the achievement progress from a specific achievement of the local player if previously set.
```
```swift
```swift
```swift
func setProgress(on: GKAchievement, to: Double)
```
```

Set a progress for an achievement for a player.
```
```swift
```swift
```swift
func setAchievementCompleted(GKAchievement)
```
```

Convenience method to set a progress to 100% for an achievement for a player.
```
```

### [Getting and removing leaderboard scores](/documentation/GameKit/GKGameActivity#Getting-and-removing-leaderboard-scores)

```swift
```swift
```swift
```swift
var leaderboardScores: Set<GKLeaderboardScore>
```
```

All leaderboard scores that have been associated with this activity.
```
```swift
```swift
```swift
func score(on: GKLeaderboard) -> GKLeaderboardScore?
```
```

Get the leaderboard score from a specific leaderboard of the local player if previously set.
```
```swift
```swift
```swift
func setScore(on: GKLeaderboard, to: Int)
```
```

Set a score of a leaderboard for a player.
```
```swift
```swift
```swift
func setScore(on: GKLeaderboard, to: Int, context: Int)
```
```

Set a score of a leaderboard with a context for a player.
```
```swift
```swift
```swift
func removeScores(from: [GKLeaderboard])
```
```

Removes all scores from leaderboards for a player if exist.
```
```

### [Getting and verifying the party code](/documentation/GameKit/GKGameActivity#Getting-and-verifying-the-party-code)

```swift
```swift
```swift
```swift
var partyCode: String?
```
```

If the game supports party code, this is the party code that can be shared among players to join the party.
```
```swift
```swift
```swift
var partyURL: URL?
```
```

If the game supports party code, this is the URL that can be shared among players to join the party.
```
```swift
```swift
```swift
class var validPartyCodeAlphabet: [String]
```
```

Allowed characters for the party code to be used to share this activity.
```
```swift
```swift
```swift
class func isValidPartyCode(String) -> Bool
```
```

Checks whether a party code is in valid format.
```
```

### [Getting the activity properties](/documentation/GameKit/GKGameActivity#Getting-the-activity-properties)

```swift
```swift
```swift
```swift
var duration: TimeInterval
```
```

Total time elapsed while in active state.
```
```swift
```swift
```swift
var startDate: Date?
```
```

The date when the activity was initially started.
```
```swift
```swift
```swift
var endDate: Date?
```
```

The date when the activity was officially ended.
```
```swift
```swift
```swift
var creationDate: Date
```
```

The date when the activity was created.
```
```swift
```swift
```swift
var lastResumeDate: Date?
```
```

The date when the activity was last resumed.
```
```

### [Getting the custom user data](/documentation/GameKit/GKGameActivity#Getting-the-custom-user-data)

```swift
```swift
```swift
```swift
var properties: [String : String]
```
```

Properties that contain additional information about the activity.
```
```

### [Getting the activity identifiers](/documentation/GameKit/GKGameActivity#Getting-the-activity-identifiers)

```swift
```swift
```swift
```swift
var identifier: String
```
```

The identifier of this activity instance.
```
```

### [Checking for an activity](/documentation/GameKit/GKGameActivity#Checking-for-an-activity)

```swift
```swift
```swift
```swift
class func checkPendingGameActivityExistence(completionHandler: (Bool) -> Void)
```
```

Checks whether there is a pending activity to handle for the current game.
```
```

### [Creating a matchmaking request](/documentation/GameKit/GKGameActivity#Creating-a-matchmaking-request)

```swift
```swift
```swift
```swift
func makeMatchRequest() -> GKMatchRequest?
```
```

Makes a `GKMatchRequest` object with information from the activity, which can be used to find matches for the local player.
```
```

### [Performing a matchmaking request](/documentation/GameKit/GKGameActivity#Performing-a-matchmaking-request)

```swift
```swift
```swift
```swift
func findMatch(completionHandler: (GKMatch?, (any Error)?) -> Void)
```
```

Use information from the activity to find matches for the local player.
```
```swift
```swift
```swift
func findPlayersForHostedMatch(completionHandler: ([GKPlayer]?, (any Error)?) -> Void)
```
```

Use information from the activity to find server hosted players for the local player.
```
```

## [Relationships](/documentation/GameKit/GKGameActivity#relationships)

### [Inherits From](/documentation/GameKit/GKGameActivity#inherits-from)

*   [`NSObject`](/documentation/ObjectiveC/NSObject-swift.class)

### [Conforms To](/documentation/GameKit/GKGameActivity#conforms-to)

*   [`CVarArg`](/documentation/Swift/CVarArg)
*   [`CustomDebugStringConvertible`](/documentation/Swift/CustomDebugStringConvertible)
*   [`CustomStringConvertible`](/documentation/Swift/CustomStringConvertible)
*   [`Equatable`](/documentation/Swift/Equatable)
*   [`Hashable`](/documentation/Swift/Hashable)
*   [`NSObjectProtocol`](/documentation/ObjectiveC/NSObjectProtocol)
*   [`Sendable`](/documentation/Swift/Sendable)
*   [`SendableMetatype`](/documentation/Swift/SendableMetatype)

## [See Also](/documentation/GameKit/GKGameActivity#see-also)

### [Activities](/documentation/GameKit/GKGameActivity#Activities)

[

Creating activities for your game](/documentation/gamekit/creating-activities-for-your-game)

Use activities to surface game content to players and encourage them to connect with each other.

```swift
```swift
```swift
class GKGameActivityDefinition
```
```

An object that represents the static metadata you define for the activity.

Beta
```
```swift
```swift
```swift
protocol GKGameActivityListener
```
```

An object that responds to activity events.

Beta
```

Beta Software

This documentation contains preliminary information about an API or technology in development. This information is subject to change, and software implemented according to this documentation should be tested with final operating system software.

[Learn more about using Apple's beta software](https://developer.apple.com/support/beta-software/)