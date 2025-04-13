

- GameKit
-  Encourage progress and competition with leaderboards 

Article

# Encourage progress and competition with leaderboards

Let players measure their own progress and compare their skills with friends and others.

## Overview

Use leaderboards to record player scores, which they can view in their Game Center account and directly in your game using built-in Game Center or custom interfaces. Game Center even encourages engagement by notifying players when their friends pass their scores.

You configure a classic or recurring leaderboard in Xcode and submit scores from your code. A *classic leaderboard* retains the scores until you delete the leaderboard. A *recurring leaderboard* automatically resets the board on the intervals you specify. For example, use a classic leaderboard for the best all-time scores and a recurring leaderboard for periodic competitions.

You can also combine individual leaderboards into sets, creating a hierarchy of leaderboards. For example, use leaderboard sets to aggregate the scores from different levels and configurations in your game. However, once you add a leaderboard set, you need to organize all other individual leaderboards into sets.

For design guidance on all types of leaderboards, see Human Interface Guidelines > Technologies > Game Center > Leaderboards. For additional information on recurring leaderboards, see Creating recurring leaderboards.

### Configure leaderboards and leaderboard sets

Before you can use leaderboards in your code, you can configure them in Xcode and sync the configuration updates you make with App Store Connect. Begin configuring leaderboards by creating a GameKit configuration file. In Xcode, choose File \> New \> File from Template. Select GameKit File, and click Next. In the sheet that appears, enter a name for the configuration and click Create.

If you’ve already configured leaderboards in App Store Connect, click More (…) at the bottom of the left column. Then choose Pull from App Store Connect. Select the bundle ID or Game Center group for your game from the list, and click pull. Resource details appear in the editor on the right.

To create a new leaderboard, click Add (+) at the bottom of the left column, and choose Leaderboard. For each leaderboard, you specify details like the score format, submission type, and whether the data resets and starts again after a period of time. Decide on a style for your leaderboard identifiers, because you won’t be able to change them at a later time. Before you begin, have at least one localized name and image, which Game Center presents to the player, ready to upload for a language.

Tip

Reorganize the list of leaderboards and leaderboard sets that Xcode displays in the order you want Game Center to present them.

A leaderboard set organizes many leaderboards into a single unit. For example, for a game with many levels, use a leaderboard set to organize the leaderboards for each level. You can have up to 100 leaderboards without using leaderboard sets. When you use leaderboard sets, you can have up to 500 leaderboards across 100 leaderboard sets.

Important

You must have at least one leaderboard for your app before you can create a leaderboard set. If you choose to use leaderboard sets, you must include all future leaderboards in a leaderboard set.

If you add a leaderboard to an unreleased version of your game or sign the game with a development certificate, Game Center annotates the leaderboard with a prerelease indicator. To change a leaderboard’s app version, see Add leaderboards to an app version.

Note

If you’ve already pushed your configuration changes to App Store Connect, removing a leaderboard or leaderboard set from the local configuration file doesn’t remove the leaderboard or leaderboard set from App Store Connect.

To learn more about the information you enter in App Store Connect, see Leaderboard properties.

### Test leaderboards by using the Progress Manager

Before you begin testing your GameKit configuration, you need to enable Debug Mode. In Xcode, choose Product \> Scheme \> Edit Scheme. From the Run configuration, select Options and toggle Enable Debug Mode.

To begin testing your leaderboard configuration, open the game Progress Manager. In Xcode, choose Debug \> GameKit \> Manage Game Progress. From the top left of the window that appears, select the physical device you use for testing, and the project you want to debug. The test data stays local to your machine and doesn’t rely on App Store Connect to test.

After selecting the device and app, choose the leaderboard you want to test. When you change a player’s score in a leaderboard, the system sends an update to your app so you can verify that the leaderboard changes.

If you want to reset the progress for your achievements and leaderboards, click the reset button at the top of the Progress Manager. You can’t access previous occurrences of achievements and leaderboards after resetting the Progress Manager.

### Choose a score format

Game Center formats the scores that you submit as integer values depending on the leaderboard configuration you enter in Xcode. On the Add Leaderboard page, choose a score format — such as fixed points, elapsed time, or money — that makes sense for your game. For example, if you choose these formats, Game Center formats the values as follows:

| Score format type | Score value | Format result |
|----|----|----|
| Fixed Point - To 1 Decimal | `1234` | `123.4` |
| Fixed Point - To 2 Decimals | `5678` | `56.78` |
| Fixed Point - To 3 Decimals | `10,000` | `10.000` |
| Elapsed Time - To the Minute | `3623` (seconds) | `60:23` |
| Elapsed Time - To the Second | `10,000` (seconds) | `2:46:40` |
| Elapsed Time - To the Hundredth of a Second | `10,000` (centiseconds) | `0:01:40:00` |
| Money - Whole Numbers | `123` | `$123` |
| Money - To 2 Decimals | `141` | `$1.41` |

Optionally, enter a range of allowable values in the Score Range fields that matches the score format. For elapsed time values, enter a range in seconds or centiseconds (Elapsed Time - To the Hundredth of a Second). For example, if you choose Elapsed Time - To the Minute and want the maximum value to be 10 minutes, enter `600` seconds in the To field. Then check whether the formatted range values that appear below the range text fields are in the score format you want.

### Add a unit to the score format or choose a currency symbol

You can further format the scores when you add a language to the leaderboard configuration in Xcode. You need to add at least one language to save the leaderboard configuration.

On the Add Language page, append a unit to the score that Game Center formats, such as `pts,` `lbs`, or `meters`, by entering the localized strings for the units in the Score Format Suffix text fields. For money values, you can choose a localized currency symbol from the Score Format menu.

### Submit scores to leaderboards

To submit a score to one or more leaderboards, use the `GKLeaderboard` submitScore(_:context:player:leaderboardIDs:completionHandler:) class method. Pass one or more leaderboard IDs, as well as the score, context, and player.

```
// Submit a score to one or more leaderboards.
try await GKLeaderboard.submitScore(points, 
                                    context: 0, 
                                    player: GKLocalPlayer.local,
                                    leaderboardIDs: ["my.leaderboard.id"]) 
```

If you load all leaderboards using the `GKLeaderboard` loadLeaderboards(IDs:completionHandler:) class method, as the next section describes, you can submit the score to specific leaderboards using the submitScore(_:context:player:completionHandler:) instance method.

Optionally, use the `context` parameter in both of these methods to store game-specific information. For example, pass a flag that contains information about how the player earned the score, such as the vehicle they drive in a racing game.

### Fetch leaderboards and leaderboard sets

To fetch one or more individual leaderboards, pass the leaderboard IDs to the `GKLeaderboard` loadLeaderboards(IDs:completionHandler:) class method.

```
// Fetch the leaderboards.
let leaderboards = try await GKLeaderboard.loadLeaderboards(IDs: ["my.leaderboard.id"])
```

To fetch specific occurrences of a recurring leaderboard, use the loadPreviousOccurrence(completionHandler:) instance method.

To fetch leaderboard sets, use the `GKLeaderboardSet` loadLeaderboardSets(completionHandler:) class method. Then to fetch individual leaderboards in a set, use the loadLeaderboards(handler:) instance method.

### Get the scores from leaderboards

To load the scores that the local player and others earn from a leaderboard, use the `GKLeaderboard` loadEntries(for:timeScope:range:completionHandler:) method.

Filter the scores using the `playerScope`, `timeScope`, and `range` parameters you pass to this method. For example, to get scores that friends of the local player earned in the past week, pass GKLeaderboard.PlayerScope.friendsOnly as the `for` parameter and GKLeaderboard.TimeScope.week as the `timeScope` parameter.

```
// Fetch the friend scores.
let result = try await leaderboard.loadEntries(for: GKLeaderboard.PlayerScope.friendsOnly,
                                               timeScope: GKLeaderboard.TimeScope.week, 
                                               range: NSMakeRange(1, 100))
```

To get all player scores in that time period, pass GKLeaderboard.PlayerScope.global as the `for` parameter instead.

Then use the properties of the GKLeaderboard.Entry instances that this method returns to get details about the individual scores, including the players who earned them.

### Display leaderboards

To display a leaderboard or leaderboard set in your custom game interface, load the leaderboard or leaderboard set and use the title property to get the localized name. To get the image representation that you upload to App Store Connect, use the loadImage(completionHandler:) method.

```
// Load the leaderboard image.
let image = try await leaderboard.loadImage()
```

Alternatively, display the leaderboard in the familiar Game Center interface. To learn more, see Display a single leaderboard.

### Set the default leaderboard

You can set the default leaderboard for an individual player during your game. For example, change the default leaderboard when the player advances to a different level in your game.

To change the local player’s default leaderboard, use the `GKLocalPlayer` setDefaultLeaderboardIdentifier(_:completionHandler:) method. To get the identifier for the default leaderboard in your code, use the loadDefaultLeaderboardIdentifier(completionHandler:) method.

Otherwise, you set the default leaderboard for all players in App Store Connect when you configure leaderboards. Xcode doesn’t support setting a default leaderboard. For the steps to change the default leaderboard in App Store Connect, see Configure leaderboards and achievements > Set a default leaderboard.

## See Also

### Leaderboards

Creating recurring leaderboards

Create a leaderboard for your game that ranks player scores based on a schedule.

Adding Recurring Leaderboards to Your Game

Encourage competition in your games by adding leaderboards that have a duration and repeat.

class GKLeaderboard

A leaderboard for a game that Game Center stores.

class GKLeaderboardSet

Organizes leaderboards into logical and coherent groups.

class GKLeaderboardScore

Information about a player’s score on a leaderboard.

