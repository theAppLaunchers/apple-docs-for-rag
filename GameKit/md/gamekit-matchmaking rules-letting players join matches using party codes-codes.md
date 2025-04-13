

- GameKit
- Matchmaking rules
-  Letting players join matches using party codes 

Article

# Letting players join matches using party codes

Add a rule that lets players invite players and join matches using a shared party code.

## Overview

You can let players start a party or group game with other players who they share a party code with. You provide an interface in your game for creating a party code, and then starting and joining matches using that party code. Then use matchmaking rules to ensure that Game Center only matches players with the same party code.

### Create a custom party code interface

In your code, implement a party code feature that:

- Generates a unique party code for the local player

- Initiates a match request from the local player using the party code

- Shares the party code with their friends and others who they want to invite

- Submits match requests from other players who receive a party code

The party code can be any combination of letters, numbers, or other characters that forms a unique identifier.

To share the party code, you can use in-game chat or data exchange in an existing match, or let the player copy the code and share outside of your game.

To submit match requests without presenting an interface using automatch, see Let Game Center match the player with others.

### Add a party code matchmaking rule

Then create a compatible rule that finds players who have the same party code.

In a compatible rule, the `requests` array in the expression contains two match requests to compare. Write an expression that returns true if the party code for the two requests is the same.

```
requests[0].properties.partyCode == requests[1].properties.partyCode
```

Create the party code rule using the Create a rule set endpoint. In the `attributes` field, set the rule’s `type` field to `COMPATIBLE` and pass the party code expression. Set the `description` and `referenceName` fields to strings that make sense for your game. In the `relationships` field, pass the `id` for the rule set in the GameCenterMatchmakingQueueCreateRequest.Data.Relationships.RuleSet.Data object.

```
POST /v1/gameCenterMatchmakingRules
{
    "data": {
        "type": "gameCenterMatchmakingRules",
        "attributes": {
            "type": "COMPATIBLE",
            "description": "Check whether the players have the same party code.",
            "referenceName": "PartyCode",
            "expression": "requests[0].properties.partyCode == requests[1].properties.partyCode"
        },
        "relationships": {
            "ruleSet": {
                "data": {
                    "type": "gameCenterMatchmakingRuleSets",
                    "id": "9e313753-2b8a-4762-b941-26f30c4184d2"
                }
            }
        }
    }
}
```

To create a rule set, see Create rule sets that contain the matchmaking rules.

### Create match requests using party codes

In your code, create a match request that initiates or joins a party by adding a `partyCode` key-value pair to the request’s `GKMatchRequest` properties dictionary.

```
// Create a match request.
let request = GKMatchRequest()

// Set the matchmaking rules queue name.
request.queueName = "com.example.mygame.PartyCodeQueue"

// Set properties to the game-specific keys you use in the rules.
request.properties = [ "partyCode": partyCode]
```

Game Center finds all compatible players in the queue that have the same party code.

## See Also

### Rules

Finding players with similar skill levels

Add a rule to find players in a range of skill levels to balance competitive gameplay.

Assigning players to teams using rules

Set criteria for assigning players to teams in your game using matchmaking rules.

Creating matchmaking rules for backward compatibility

Add matchmaking rules that support previous classic matchmaking versions of your game.

