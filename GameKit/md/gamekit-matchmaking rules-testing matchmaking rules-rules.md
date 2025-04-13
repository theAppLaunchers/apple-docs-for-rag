

- GameKit
- Matchmaking rules
-  Testing matchmaking rules 

Article

# Testing matchmaking rules

Test your matchmaking rules before you use them in your game.

## Overview

Before you write any code, you can test your matchmaking rules on the server side to ensure that they find compatible players without long wait times. You pass the rule set and sample match requests to the test API, and it responds with the match results.

To download a script that helps test your matchmaking rules, see Testing matchmaking rules using a Python script. For examples using the script, see Meet rule-based matchmaking in Game Center.

### Create sample match requests

Create an array of GameCenterMatchmakingTestRequestInlineCreate objects that represent sample match requests. Set the `type` field to `gameCenterMatchmakingTestRequests` and the `id` field to a unique identifier for the match request.

The `attributes` field has the same fields as the `Request` object that you use in expressions. Set the required `requestName` field to a unique string and the `bundleId` field to your game’s bundle identifier. Set the `platform` and `appVersion` fields to appropriate values, such as `1.0` and `IOS`. Set the `secondsInQueue` field to `0` unless you want to test rules with different match request ages.

```
"included": [
        {
            "type": "gameCenterMatchmakingTestRequests",
            "id": "${r1}",
            "attributes": {
                "requestName": "r1",
                "appVersion": "1.0.0",
                "bundleId": "com.example.mygame",
                "platform": "IOS",
                "secondsInQueue": 0
            },
            "relationships": {
                "matchmakingPlayerProperties": {
                    "data": [
                        {
                            "type": "gameCenterMatchmakingTestPlayerProperties",
                            "id": "${r1_p1}"
                        }
                    ]
                }
            }
        },
        {
            "type": "gameCenterMatchmakingTestRequests",
            "id": "${r2}",
            "attributes": {
                "requestName": "r2",
                "appVersion": "1.0.0",
                "bundleId": "com.example.mygame",
                "platform": "IOS",
                "secondsInQueue": 0
            },
            "relationships": {
                "matchmakingPlayerProperties": {
                    "data": [
                        {
                            "type": "gameCenterMatchmakingTestPlayerProperties",
                            "id": "${r2_p1}"
                        }
                    ]
                }
            }
        },
...
```

In the `relationships` field, include resource objects for any game-specific properties that you use in the expressions. For example, if you’re testing party code rules, described in Letting players join matches using party codes, add a GameCenterMatchmakingTestRequestInlineCreate.Relationships.MatchmakingPlayerProperties object to each match request.

Then append a corresponding GameCenterMatchmakingTestPlayerPropertyInlineCreate object for each of the match request. In the `attributes` field, provide a key-value pair for each property, such as the `partyCode` property.

```
...
        {
            "type": "gameCenterMatchmakingTestPlayerProperties",
            "id": "${r1_p1}",
            "attributes": {
                "properties": [
                    {
                        "key": "partyCode",
                        "value": "\"Q1R5A6T9\""
                    }
                ],
                "playerId": "r1_p1"
            }
        },
        {
            "type": "gameCenterMatchmakingTestPlayerProperties",
            "id": "${r2_p1}",
            "attributes": {
                "properties": [
                    {
                        "key": "partyCode",
                        "value": "\"Q1R5A6T9\""
                    }
                ],
                "playerId": "r2_p1"
            }
        }
    ]
}
```

### Test the matchmaking rules

Apply the matchmaking rules by passing the associated rule set and the sample match requests to the Test a rule set endpoint. Pass the rule set `id` using the `matchmakingRuleSet` field and pass resource objects representing the match requests in the `matchmakingRequests` field. Then pass the array of GameCenterMatchmakingTestRequestInlineCreate and GameCenterMatchmakingTestPlayerPropertyInlineCreate objects, that you create above, in the `included` field.

```
POST /v1/gameCenterMatchmakingRuleSetTests
{
    "data": {
        "type": "gameCenterMatchmakingRuleSetTests",
        "attributes": {},
        "relationships": {
            "matchmakingRuleSet": {
                "data": {
                    "type": "gameCenterMatchmakingRuleSets",
                    "id": "9e313753-2b8a-4762-b941-26f30c4184d2"
                }
            },
            "matchmakingRequests": {
                "data": [
                    {
                        "type": "gameCenterMatchmakingTestRequests",
                        "id": "${r1}"
                    },
                    {
                        "type": "gameCenterMatchmakingTestRequests",
                        "id": "${r2}"
                    }
                ]
            }
        }
    },
    "included": [...}
}
```

The endpoint response contains the matchmaking results. Parse the `matchmakingResults` array in the GameCenterMatchmakingRuleSetTest.Attributes object. If the rule set contains team rules, the team assignments appear in the `teamAssignments` field of the GameCenterMatchmakingRuleSetTest.Attributes.MatchmakingResults object.

```
{
    "data": {
        "type": "gameCenterMatchmakingRuleSetTests",
        "attributes": {
            "matchmakingResults": [
                [
                    {
                        "requestName": "r1",
                        "teamAssignments": null
                    },
                    {
                        "requestName": "r2",
                        "teamAssignments": null
                    }
                ]
            ]
        },
...
```

To create a rule set, see Create rule sets that contain the matchmaking rules, and to create team rules, see Assigning players to teams using rules.

## See Also

### Testing

Troubleshooting matchmaking rules using metrics

Investigate issues with Game Center by evaluating your matchmaking rules using metrics endpoints.

Testing rule sets with player traffic using metrics

Get metrics on a new rule set with real match requests before releasing it.

