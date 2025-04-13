

- GameKit
- Matchmaking rules
-  Testing rule sets with player traffic using metrics 

Article

# Testing rule sets with player traffic using metrics

Get metrics on a new rule set with real match requests before releasing it.

## Overview

Before you update the rule set of a queue that actively processes player match requests, make sure that the new rule set doesn’t introduce any performance regressions. Game Center provides APIs to evaluate the performance of a prerelease rule set with production match requests that the queue actively processes, without impacting the player experience.

### Add an experimental rule set to a queue

You can add an optional experimental rule set to a queue, in addition to the required rule set that Game Center uses in production. When you add an experimental rule set, Game Center processes the match requests in the queue using both the existing rule set and the experimental rule set, except that it doesn’t return the results of the experimental rule set to clients. So you can apply the same metrics APIs on the experimental rule set to analyze performance issues before you release it.

To set the experimental rule set of a queue, use the Modify a queue endpoint. Pass the queue’s identifier in the path parameters and include the experimental rule set’s identifier in the request body.

```
PATCH /v1/gameCenterMatchmakingQueues/532ad9c0-1a28-4536-ad57-33213bcc0a29
{
  "data" : {
    "type" : "gameCenterMatchmakingQueues",
    "id" : "532ad9c0-1a28-4536-ad57-33213bcc0a29"
    "relationships" : {
      "experimentRuleSet" : {
        "data" : { "type": "gameCenterMatchmakingRuleSet", "id": "6195839b-4ef7-4798-b91d-d59802111607" }
      }
    }
  }
}
```

Game Center uses the experimental rule set for next three days. If you want to use the experimental rule set longer, add it to the queue every three days until you’re done testing it.

To create a new rule set and get its identifier, see Finding players using matchmaking rules.

### View the results of an experimental rule set

To get the results of processing match requests using the experimental rule set, pass `experimentalRuleSet` in the query parameter to the List all queues or Read queue information endpoints. Then compare the results of the experimental rule set with the production rule set.

```
GET /v1/gameCenterMatchmakingQueues/532ad9c0-1a28-4536-ad57-33213bcc0a29/experimentMatchmakingRequests?granularity=PT15M&groupBy=result
```

If it takes Game Center longer to find players or Game Center finds fewer players with the experimental rule set, check whether errors occur applying the rules and consider relaxing the rule conditions. For more information, see Troubleshooting matchmaking rules using metrics.

### Check the size of the queue

Also, check the queue size over time using the Get experimental queue size endpoint. If the queue size for the experimental rule set is larger than the queue size for the existing rule set, investigate whether the new rule set causes this before releasing it.

```
GET /v1/gameCenterMatchmakingQueues/532ad9c0-1a28-4536-ad57-33213bcc0a29/metrics/experimentMatchmakingQueueSizes?granularity=PT15M
```

### Release the new rule set

After you finish testing the new rule set, release it by replacing the queue’s rule set with the new one.

First, remove the experimental rule set that you used for testing from the queue using the Modify a queue endpoint. Pass the queue identifier in the parameters and set `data` to `null` in the request body.

```
PATCH /v1/gameCenterMatchmakingQueues/532ad9c0-1a28-4536-ad57-33213bcc0a29/relationships/experimentRuleSet
{
   "data" : null
}
```

Then set the queue’s rule set using the Modify a queue endpoint. Pass the queue identifier in the parameters and include the new rule set’s identifier in the request body.

```
PATCH /v1/gameCenterMatchmakingQueues/532ad9c0-1a28-4536-ad57-33213bcc0a29
{
  "data" : {
    "type" : "gameCenterMatchmakingQueues",
    "id" : "532ad9c0-1a28-4536-ad57-33213bcc0a29"
    "relationships" : {
      "ruleSet" : {
        "data" : { "type": "gameCenterMatchmakingRuleSet", "id": "6195839b-4ef7-4798-b91d-d59802111607" }
      }
    }
  }
}
```

## See Also

### Testing

Testing matchmaking rules

Test your matchmaking rules before you use them in your game.

Troubleshooting matchmaking rules using metrics

Investigate issues with Game Center by evaluating your matchmaking rules using metrics endpoints.

