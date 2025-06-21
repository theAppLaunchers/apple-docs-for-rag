Framework

# GameKit

Enable players to interact with friends, compare leaderboard ranks, earn achievements, and participate in multiplayer games.

iOS 3.0+iPadOS 3.0+Mac Catalyst 13.1+macOS 10.8+tvOS 9.0+visionOS 1.0+watchOS 3.0+

## [Overview](/documentation/GameKit#overview)

Use the GameKit framework to implement Game Center social-gaming network features. Game Center is an Apple service that provides a single account that identifies players across all their games and devices. After players sign in to Game Center on their device, they can access their friends and use Game Center features you implement.

![Multiple iPhone screens showing these Game Center features: an access point, achievement dashboard, leaderboard dashboard, and inviting friends.](https://docs-assets.developer.apple.com/published/febd437ebe02ea5bbae565532b9fc83c/media-4091475%402x.png)

Before you can use GameKit classes, you must enable Game Center in your project and initialize the local player in your code; otherwise, your game receives a [`GKError.Code.notAuthenticated`](/documentation/gamekit/gkerror/code/notauthenticated) error.

If you have an existing Unity project, you can access the GameKit framework using the [Apple Unity Plug-ins](https://github.com/Apple/UnityPlugins).

### [Implement Game Center features](/documentation/GameKit#Implement-Game-Center-features)

After you’ve enabled Game Center, you can implement many useful features to enhance the gaming experience.

You can add leaderboards that let players see how well they rank amongst friends and players all over the world. Create recurring leaderboards to organize regular competitions that provide players more chances to earn the top score. As players progress through your game, you can reward them with achievements that encourage them to keep playing.

GameKit supports real-time and turn-based multiplayer experiences. Players can choose automatic matching or invite their friends to join a game. You can support turn-based gaming in which a match plays out over a series of alternating turns, and players can receive invitations even when your game isn’t in the foreground.

GameKit also provides user interface components for your players to see highlights and access their Game Center data directly in your game. The access point provides a way for players to open a dashboard in which they can browse their profile, leaderboards, and achievements, as well as manage their friends list.

For designing Game Center features in your app, see [Human Interface Guidelines > Technologies > Game Center](https://developer.apple.com/design/human-interface-guidelines/game-center).

## [Topics](/documentation/GameKit#topics)

### [Essentials](/documentation/GameKit#Essentials)

[

Initializing and configuring Game Center](/documentation/gamekit/initializing-and-configuring-game-center)

Enable Game Center in your Xcode project and configure features in App Store Connect.

[

Authenticating a player](/documentation/gamekit/authenticating-a-player)

Confirm player credentials and device capabilities and check for account restrictions.

[

Improving the player experience for games with large downloads](/documentation/gamekit/improving-the-player-experience-for-games-with-large-downloads)

Provide ample content in your base installation and then use on-demand resources and the Background Assets API to handle additional content.

[`Game Center Entitlement`](/documentation/BundleResources/Entitlements/com.apple.developer.game-center)

A Boolean value that indicates whether users of the app may see and compare achievements on a leaderboard, invite friends, and start multiplayer games.

### [Players](/documentation/GameKit#Players)

[

Connecting players with their friends in your game](/documentation/gamekit/connecting-players-with-their-friends-in-your-game)

Give players the ability to connect and interact with friends in your game.

[

Saving the player’s game data to an iCloud account](/documentation/gamekit/saving-the-player-s-game-data-to-an-icloud-account)

Save game data during play or after a game in the player’s iCloud account that’s accessible from any device.

[

Protecting the player’s privacy using scoped identifiers](/documentation/gamekit/protecting-the-player-s-privacy-using-scoped-identifiers)

Use the scoped identifiers that GameKit provides you as player IDs when transmitting or saving player data.

```swift
```swift
```swift
class GKLocalPlayer
```
```

The local player who signs in to Game Center on the device running the game.
```
```swift
```swift
```swift
class GKPlayer
```
```

A remote player who the local player running your game can invite and communicate with through Game Center.
```
```swift
```swift
```swift
class GKBasePlayer
```
```

A class that provides common data and methods for the different player objects.
```
```swift
```swift
```swift
protocol GKLocalPlayerListener
```
```

A protocol that handles events for Game Center players.
```

[`static let GKPlayerAuthenticationDidChangeNotificationName: NSNotification.Name`](/documentation/Foundation/NSNotification/Name-swift.struct/GKPlayerAuthenticationDidChangeNotificationName)

A notification that posts after GameKit authenticates the local player.

[`static let GKPlayerDidChangeNotificationName: NSNotification.Name`](/documentation/Foundation/NSNotification/Name-swift.struct/GKPlayerDidChangeNotificationName)

A notification that posts when a player object’s data changes.

### [Game Center interfaces](/documentation/GameKit#Game-Center-interfaces)

[

Adding an access point to your game](/documentation/gamekit/adding-an-access-point-to-your-game)

Provide your users a convenient connection to the Game Center dashboard.

[

Displaying the Game Center dashboard](/documentation/gamekit/displaying-the-game-center-dashboard)

Provide an interface for players to navigate to their Game Center data from your game.

```swift
```swift
```swift
class GKAccessPoint
```
```

An object that allows players to view and manage their Game Center information from within your game.
```
```swift
```swift
```swift
class GKDialogController
```
```

An object that provides the ability to present the dashboard in macOS games.
```
```swift
```swift
```swift
protocol GKViewController
```
```

The abstract base protocol adopted by GameKit view controller classes.
```

### [Leaderboards](/documentation/GameKit#Leaderboards)

[

Encourage progress and competition with leaderboards](/documentation/gamekit/encourage-progress-and-competition-with-leaderboards)

Let players measure their own progress and compare their skills with friends and others.

[

Creating recurring leaderboards](/documentation/gamekit/creating-recurring-leaderboards)

Create a leaderboard for your game that ranks player scores based on a schedule.

[

Adding Recurring Leaderboards to Your Game](/documentation/gamekit/adding-recurring-leaderboards-to-your-game)

Encourage competition in your games by adding leaderboards that have a duration and repeat.

```swift
```swift
```swift
class GKLeaderboard
```
```

A leaderboard for a game that Game Center stores.
```
```swift
```swift
```swift
class GKLeaderboardSet
```
```

Organizes leaderboards into logical and coherent groups.
```
```swift
```swift
```swift
class GKLeaderboardScore
```
```

Information about a player’s score on a leaderboard.
```

### [Achievements](/documentation/GameKit#Achievements)

[

Rewarding players with achievements](/documentation/gamekit/rewarding-players-with-achievements)

Use achievements to motivate players and engage them more in your game.

```swift
```swift
```swift
class GKAchievement
```
```

An achievement you can award a player as they make progress toward and reach a goal in your game.
```
```swift
```swift
```swift
class GKAchievementDescription
```
```

An object containing the text and artwork used to present an achievement to a player.
```

### [Challenges](/documentation/GameKit#Challenges)

[

Creating engaging challenges from leaderboards](/documentation/gamekit/creating-engaging-challenges-from-leaderboards)

Encourage friendly competition by adding challenges to your game.

[

Choosing a leaderboard for your challenges](/documentation/gamekit/choosing-a-leaderboard-for-your-challenges)

Understand what gameplay works well when configuring challenges in your game.

```swift
```swift
```swift
class GKChallengeDefinition
```
```

An object that represents the static metadata you define for the challenge.

Beta
```

[`GKShowChallengeBanners`](/documentation/BundleResources/Information-Property-List/GKShowChallengeBanners)

A Boolean value that indicates whether GameKit can display challenge banners in a game.

### [Activities](/documentation/GameKit#Activities)

[

Creating activities for your game](/documentation/gamekit/creating-activities-for-your-game)

Use activities to surface game content to players and encourage them to connect with each other.

```swift
```swift
```swift
class GKGameActivity
```
```

An object that represents a single instance of a game activity for the current game.

Beta
```
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

### [Real-time games](/documentation/GameKit#Real-time-games)

[

Creating real-time games](/documentation/gamekit/creating-real-time-games)

Develop games where multiple players interact in real time.

[

Finding multiple players for a game](/documentation/gamekit/finding-multiple-players-for-a-game)

Discover and invite other players to participate in a real-time game.

[

Exchanging data between players in real-time games](/documentation/gamekit/exchanging-data-between-players-in-real-time-games)

Send data between players in a real-time multiplayer game.

[

Adding voice chat to multiplayer games](/documentation/gamekit/adding-voice-chat-to-multiplayer-games)

Enable players to voice chat with all, or groups of, players in a multiplayer game.

[

API Reference

Matchmaking rules](/documentation/gamekit/matchmaking-rules)

Game Center applies different type of rules you create in a particular order to find the best matches.

```swift
```swift
```swift
class GKMatchRequest
```
```

An object that encapsulates the parameters to create a real-time or turn-based match.
```
```swift
```swift
```swift
class GKMatchmaker
```
```

An object that creates matches with other players without presenting an interface to the players.
```
```swift
```swift
```swift
class GKMatchmakerViewController
```
```

An interface that allows a player to invite other players to a real-time game and automatch to fill any empty slots.
```
```swift
```swift
```swift
protocol GKInviteEventListener
```
```

A protocol that handles invite events from Game Center.
```
```swift
```swift
```swift
class GKInvite
```
```

An invitation to join a match sent to the local player from another player.
```
```swift
```swift
```swift
class GKMatch
```
```

A peer-to-peer network between a group of players that sign into Game Center.
```

### [Turn-based games](/documentation/GameKit#Turn-based-games)

[

Creating turn-based games](/documentation/gamekit/creating-turn-based-games)

Develop games where multiple players take turns and can exchange data while waiting for their turn.

[

Starting turn-based matches and passing turns between players](/documentation/gamekit/starting-turn-based-matches-and-passing-turns-between-players)

Let Game Center store and forward match data between players in a turn-based game.

[

Sending messages to players in turn-based games](/documentation/gamekit/sending-messages-to-players-in-turn-based-games)

Notify players of match events by sending messages and game data.

[

Exchanging data between players in turn-based games](/documentation/gamekit/exchanging-data-between-players-in-turn-based-games)

Add the ability for players to exchange game data and send messages while waiting for their turns.

```swift
```swift
```swift
class GKTurnBasedMatchmakerViewController
```
```

An interface that allows a player to invite other players to a turn-based match and automatch to fill any empty slots.
```
```swift
```swift
```swift
class GKTurnBasedMatch
```
```

An object that encapsulates the match data for games where players take turns.
```
```swift
```swift
```swift
class GKTurnBasedParticipant
```
```

A participant in a turn-based match.
```
```swift
```swift
```swift
protocol GKTurnBasedEventListener
```
```

The protocol that handles turn-based and data-exchange events between participants in a match.
```
```swift
```swift
```swift
class GKTurnBasedExchange
```
```

Exchange request information that participants send in a turn-based match.
```
```swift
```swift
```swift
class GKTurnBasedExchangeReply
```
```

Details about a recipient’s response to an exchange request.
```

[`GKGameCenterBadgingDisabled`](/documentation/BundleResources/Information-Property-List/GKGameCenterBadgingDisabled)

A Boolean value indicating whether GameKit can add badges to a turn-based game icon.

### [Errors](/documentation/GameKit#Errors)

```swift
```swift
```swift
```swift
struct GKError
```
```

The error structure used by this framework.
```
```swift
```swift
```swift
enum Code
```
```

Error codes for the GameKit error domain.
```
```swift
```swift
```swift
let GKErrorDomain: String
```
```

The error domain for general game errors.
```
```

### [Deprecated](/documentation/GameKit#Deprecated)

[

API Reference

Deprecated symbols](/documentation/gamekit/deprecated-symbols)

Review unsupported symbols and their replacements.