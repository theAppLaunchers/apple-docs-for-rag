

- GameKit
- Matchmaking rules
-  Creating matchmaking rules for backward compatibility 

Article

# Creating matchmaking rules for backward compatibility

Add matchmaking rules that support previous classic matchmaking versions of your game.

## Overview

Let players running the current version of your game match with players running previous classic matchmaking versions that don’t use rules. You increase the pool of players, improve the quality of matches, and reduce wait times, if you configure a queue and write rules that include classic match requests.

For more information on creating queues, rule sets, and rules, see Finding players using matchmaking rules.

### Add classic match requests to a queue

Game Center adds classic match requests that don’t specify a queue name to a default classic matchmaking queue, excluding the requests from matching with players running versions that use rules. To include classic match requests in a queue, set the `classicMatchmakingBundleIds` field to the bundle IDs of the versions you want to include when you create the queue using the Create a queue endpoint.

```
POST /v1/gameCenterMatchmakingQueues
{
    "data": {
        "type": "gameCenterMatchmakingQueues",
        "attributes": {
            "referenceName": "com.example.mygame.ClassicSkillRules"
            "classicMatchmakingBundleIds": [ "com.example.mygame" ]
        },
        "relationships": {
            "ruleSet": {
                "data": {
                    "type": "gameCenterMatchmakingRuleSets",
                    "id": "6f7c8f9a-18ba-4372-9c17-d3fa0d18c46c"
                }
            }
        }
    }
}
```

If you create a Game Center group in App Store Connect to share leaderboards, achievements, and matchmaking between games (see Create groups), add the bundle IDs for the classic matchmaking games in the group to the `classicMatchmakingBundleIds` property.

### Add a rule that handles the player group property

If you set the player group property of match requests in classic matchmaking versions, add a compatible rule to the rule set and queue that matches requests by player group.

When you add classic match requests to a queue with the playerGroup property set, those requests contain a `playerGroup` property in the `properties` array. Add a rule with a Boolean expression that compares the `playerGroup` properties of two requests using the Create a rule endpoint.

```
POST /v1/gameCenterMatchmakingRules
{
    "data": {
        "type": "gameCenterMatchmakingRules",
        "attributes": {
            "type": "COMPATIBLE",
            "description": "Players must use same map",
            "referenceName": "SameMap",
            "expression": "requests[0].properties.playerGroup == requests[1].properties.playerGroup"
        },
        "relationships": {
            "ruleSet": {
                "data": {
                    "type": "gameCenterMatchmakingRuleSets",
                    "id": "56f6cee1-df7b-45df-9bdc-c60d1208b3bf"
                }
            }
        }
    }
}
```

In versions of your game that use matchmaking rules, be sure to include a corresponding `playerGroup` property in match requests using the properties property.

For more information on creating rules, see Add matchmaking rules to the rule sets.

### Write expressions that provide default values for player properties

If your rules use player properties that previous versions of your game don’t supply, the rules won’t match players of the previous versions with the current version. Especially if you configure a queue to contain both classic and rule-based match requests, the classic requests won’t have your custom player properties. To provide backward compatibility with previous versions, write rule expressions in a way that provide default values for missing player properties.

For example, replace this expression for the skills-based match rule (see Finding players with similar skill levels) with one that provides a default value for the `skill` property:

```
diff(players[].properties.skill) 

Use the rich set of JMESPath operators, expressions, and functions in the rule expression to achieve the desired results. For example, this expression uses the flatten operator, wildcard expression, pipe expression, and `not_null()` function to provide a default value of 50 for the `skill` property:

```
requests[].properties.[ skill, `50`][*].not_null(@) | [*][0]
```

To understand this and other complex expressions before adding them to rules, use the JMESPath playground. For example, create sample requests where one player has a skill level of `49` and another player has no `skill` property value (see Create JMESPath playground sample match requests). Enter the sample requests into the input JSON field of the playground. Then enter parts of the expression in the playground to see the results.

| Expression | Result |
|----|----|
| `requests[].properties` | `[ 49 ]` |
| `requests[].properties.[ skill, `50`]` | `[ [ 49, 50 ], [ null, 50 ] ]` |
| `requests[].properties.[ skill, `50\`\]\[\*\].not_null(@) | \[\*\]\[0\]\` |

Add the expression that produces the desired results to a rule using the Create a rule endpoint. For example, replace the Boolean expression above that uses the `diff()` function to compare player skill properties with one that provides a default value for the `skill` property (see Create a match rule containing the expression).

```
diff(requests[].properties.[ skill, `50`][*].not_null(@) | [*][0]) 

### Create JMESPath playground sample match requests

Sample match requests that you create for testing expressions in the JMESPath playground are similar to those you pass to the Test a rule set endpoint. Pass the same attribute and relationship properties except without the enclosing Game Center data structures.

For example, create sample requests where one player has a skill level of `49` and another player has no `skill` property value. For examples of match requests that you pass to the testing APIs, see Testing matchmaking rules.

To create sample match requests for the playground using a script, see Testing matchmaking rules using a Python script.

```
{
    "requests": [
        {
            "requestName": "r1",
            "playerId": "r1_p1",
            "properties": {
                "skill": 49
            },
            "players": [
                {
                    "playerId": "r1_p1",
                    "properties": {
                        "skill": 49
                    },
                    "requestName": "r1"
                }
            ],
            "appVersion": "1.0.0",
            "bundleId": "com.example.mygame",
            "platform": "IOS",
            "locale": "EN-US",
            "longitude": 0,
            "latitude": 0,
            "minPlayers": 2,
            "maxPlayers": 2,
            "playerCount": 1,
            "secondsInQueue": 0
        },
        {
            "requestName": "r2",
            "playerId": "r2_p1",
            "properties": {},
            "players": [
                {
                    "playerId": "r2_p1",
                    "properties": {},
                    "requestName": "r2"
                }
            ],
            "appVersion": "1.0.0",
            "bundleId": "com.example.mygame",
            "platform": "IOS",
            "locale": "EN-US",
            "longitude": 0,
            "latitude": 0,
            "minPlayers": 2,
            "maxPlayers": 2,
            "playerCount": 1,
            "secondsInQueue": 0
        }
    ],
    "players": [
        {
            "playerId": "r1_p1",
            "properties": {
                "skill": 49
            },
            "requestName": "r1"
        },
        {
            "playerId": "r2_p1",
            "properties": {},
            "requestName": "r2"
        }
    ]
}
```

### Test match requests from previous versions

Test your matchmaking rules on the server side with different combinations of match requests from previous and current versions of your game. Pass the rule set and sample match requests to the test API (see Testing matchmaking rules). Your rules should match players using different versions of your game.

## See Also

### Rules

Letting players join matches using party codes

Add a rule that lets players invite players and join matches using a shared party code.

Finding players with similar skill levels

Add a rule to find players in a range of skill levels to balance competitive gameplay.

Assigning players to teams using rules

Set criteria for assigning players to teams in your game using matchmaking rules.

