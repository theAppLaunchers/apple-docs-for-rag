

- GameKit
- Matchmaking rules
-  Finding players with similar skill levels 

Article

# Finding players with similar skill levels

Add a rule to find players in a range of skill levels to balance competitive gameplay.

## Overview

When finding players using matchmaking rules, consider adding a rule that finds players in a range of skill levels to make gameplay more enjoyable and fair for all players. To reduce wait times for players, make the rule widen the skill range as the wait time, or age of the match request, increases.

This article shows one way to find players by skill level that you can combine with your other matchmaking rules. For other types of matchmaking rules, see Letting players join matches using party codes and Assigning players to teams using rules.

### Create a skill-level rule set and queue

First create a rule set to contain the skill-level rule. Pass a reference name, the minimum players, and the maximum players properties that are game-specific to the Create a rule set endpoint.

```
POST /v1/gameCenterMatchmakingRuleSets
{
    "data": {
        "type": "gameCenterMatchmakingRuleSets",
        "attributes": {
            "referenceName": "com.example.mygame.SkillBasedRules",
            "ruleLanguageVersion": 1,
            "minPlayers": 2,
            "maxPlayers": 4
        },
        "relationships": {}
    }
}
```

Retain the `id` field of the GameCenterMatchmakingRuleSet object that this endpoint returns to use later when you create the skill-level rule.

```
{
    "data": {
        "type": "gameCenterMatchmakingRuleSets",
        "id": "36c540f2-031a-4e35-8260-d0804e40376b",
        "attributes": {
            "referenceName": "com.example.mygame.SkillBasedRules",
            "ruleLanguageVersion": 1,
            "minPlayers": 2,
            "maxPlayers": 4
        },
...
}
```

Then create and add the rule set to a skill-level queue. Pass a reference name and the rule set that you create to the Create a queue endpoint. Pass the `id` for the rule set in the GameCenterMatchmakingQueueCreateRequest.Data.Relationships.RuleSet.Data object.

```
POST /v1/gameCenterMatchmakingQueues
{
    "data": {
        "type": "gameCenterMatchmakingQueues",
        "attributes": {
            "referenceName": "com.example.mygame.SkillBasedRules"
        },
        "relationships": {
            "ruleSet": {
                "data": {
                    "type": "gameCenterMatchmakingRuleSets",
                    "id": "36c540f2-031a-4e35-8260-d0804e40376b"
                }
            }
        }
    }
}
```

### Choose parameters that work best for your game

You can create a matchmaking rule that initially attempts to match players with similar skill values, then after a few seconds, increases the skill range for another period of seconds. The rule repeats the increments at specified intervals until it reaches a maximum difference in skill levels.

For example, if the skill of players ranges from `0` to `100` in your game, create a rule that:

- For the first `10` seconds, tries to find players with an ideal `20` points or less difference in skill level.

- For the next `10` seconds, compromises to find players within `40` points or less difference in skill level.

- After `20` seconds, finds players with no more than the maximum `100` points difference.

You choose the number of increments and the ranges of wait times and skill levels.

### Write an expression that matches players by skill level

Write an expression for a match rule where the expression returns a Boolean value of true for an acceptable range of skill values that expands at specified time increments. An expression is a JMESPath formatted string with some Game Center matchmaking function additions.

First use the `diff()` function (see Computing numeric differences) to compute the difference between the maximum and minimum skill values of players, where `skill` is a game-specific property name that you set in your code when you submit a match request.

```
diff(players[].properties.skill)
```

In a match rule, the requests array contains only compatible matches because Game Center applies compatible and distance rules before match rules.

Then use the `agedValues()` function to return a range of desired skill values depending on the average wait time or age of the requests. Compute the average age of the requests using the `avg()` function.

```
avg(requests[].secondsInQueue)
```

Pass the average age as the first parameter to the `agedValues()` function and other parameters depending on your game (see Getting value based on age using an array).

For example, if the ideal difference in skill is `20`, pass `20` as the `initialValue` parameter. Then pass an array of age increments as the `ages` parameter (`[ `10`, `20` ]`) and corresponding skill differences as the `values` parameter (`[ `40`, `100` ]`) to the `agedValues()` function.

```
agedValues(avg(requests[].secondsInQueue), `20`, [ `40`, `100` ], [ `10`, `20` ])
```

Now compose a Boolean expression that compares the maximum difference in skill between compatible requests with the desired difference in skill as a function of wait time.

```
diff(players[].properties.skill) 

For more information on the Game Center functions you can use in expressions, see Expressions in App Store Connect API.

Important

If you have previous versions of your game that don’t provide player properties used in your rules, you can write expressions that provide default value for those properties. See Creating matchmaking rules for backward compatibility.

### Create a match rule containing the expression

Create a skill-level rule and add it to the rule set. Pass `MATCH` for the rule `type` field, the skill-level expression, and the rule set, along with other settings, to the Create a rule \`\`endpoint.

```
POST /v1/gameCenterMatchmakingRules
{
    "data": {
        "type": "gameCenterMatchmakingRules",
        "attributes": {
            "type": "MATCH",
            "description": "Players must have skill in given range",
            "referenceName": "SkillDifference",
            "expression": "diff(players[].properties.skill) 

The `description` and `referenceName` fields are specific to your game. In the `relationships` field, pass the `id` for the rule set in the `GameCenterMatchmakingQueueCreateRequest.Data.Relationships.RuleSet.Data` object.

Note

Typically, you add more than one rule to a rule set. For example, add a `COMPATIBLE` rule to check whether the player’s app versions are the same and a `DISTANCE` rule to find players nearby that Game Center applies before `MATCH` rules.

### Submit a skill-level match request

In your code, create a GKMatchRequest object that uses the skill-level queue and its set of rules to find players. Set the properties and queueName properties of the match request, so that Game Center uses the matchmaking rules to find players.

```
// Create a match request.
let request = GKMatchRequest()
```

Set the queueName property to the reference name of the queue that you previously created using the `Create a queue` endpoint.

```
// Set the matchmaking rules queue name.
request.queueName = "com.example.mygame.SkillBasedRules"
```

Set properties to a dictionary of key-value pairs that provide values you can use in expressions. Add a `skill` key with a value that represents the local player’s skill level.

```
// Set properties to the game-specific keys you use in the rules.
let skill = localPlayerData.skill
request.properties = [ "skill": skill]
```

If you set the recipients property, you can also set skill levels for each recipient using the recipientProperties property.

Then submit the match request using the same APIs regardless of whether you configure matchmaking rules. For example, present the GKMatchmakerViewController interface or use the GKMatchmaker class that finds players using automatch without presenting an interface.

When all the players accept their invitations and GameKit invokes the matchmakerViewController(_:didFind:) delegate method in the app instances for all players in the game, you can access the skill levels of all the players using the `GKMatch.playerProperties` property.

For more information, see Finding multiple players for a game.

## See Also

### Rules

Letting players join matches using party codes

Add a rule that lets players invite players and join matches using a shared party code.

Assigning players to teams using rules

Set criteria for assigning players to teams in your game using matchmaking rules.

Creating matchmaking rules for backward compatibility

Add matchmaking rules that support previous classic matchmaking versions of your game.

