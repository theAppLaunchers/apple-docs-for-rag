

- GameKit
-  Exchanging data between players in turn-based games 

Article

# Exchanging data between players in turn-based games

Add the ability for players to exchange game data and send messages while waiting for their turns.

## Overview

You can increase engagement in turn-based games by letting participants communicate and exchange data while they wait for the current participant to take their turn.

To implement this feature, provide an interface in your game where participants can communicate — for example, exchange items in the game. Then initiate an exchange request from the user of your game instance, called the *local player*, to one or more recipients. GameKit handles the requests between participants and the status of the exchange object as participants reply. You implement protocol methods to accept exchanges, display results, and save completed exchanges. When you save completed exchanges, GameKit notifies all other participants.

To receive the protocol messages, register as a listener of the local player, and conform to the GKTurnBasedEventListener protocol. For more information, see Starting turn-based matches and passing turns between players.

```
GKLocalPlayer.local.register(self)
```

Important

The code examples in this article use GameKit asynchronous methods that you invoke from an `async` method or within a `Task` structure. For details about asynchronous flows, see Concurrency.

### Send exchange requests

Any participant, including the current participant who is taking their turn, can send an exchange request to one or more other participants. When sending an exchange request, you pass the recipients, the game-specific exchange data, and a localized message to the `GKTurnBasedMatch` sendExchange(to:data:localizableMessageKey:arguments:timeout:completionHandler:) method.

```
try await match.sendExchange(to: participants, data: data!, localizableMessageKey: 
   "This is my exchange request.", arguments: [], timeout: GKTurnTimeoutDefault)
```

In the exchange data, provide enough game-specific information for recipients to decide whether to accept or decline the request.

To localize the message, add the key you pass and a placeholder translation to a `.strings` file in your project (for example, the default `Localizable.strings` file). For more information about adapting your game for different languages and regions, see Localization.

### Respond to exchange requests

When a recipient receives an exchange request, GameKit invokes the `GKTurnBasedEventListener` player(_:receivedExchangeRequest:for:) protocol method, passing the exchange object. If your game isn’t running or is in the background, GameKit displays a notification containing the localized message first. When the recipient taps the notification, GameKit launches your game or brings your game back to the foreground, and then invokes the method.

To accept or decline the exchange request on behalf of the participant, implement the player(_:receivedExchangeRequest:for:) method using the following steps:

1.  Unarchive the exchange data in the GKTurnBasedExchange object that GameKit passes to this method.

2.  If the status property is GKTurnBasedExchangeStatus.active, present an interface containing the exchange data that lets the recipient accept or decline the request.

3.  To display more details to the recipient, use the other `GKTurnBasedExchange` properties, such as the sender and message properties.

4.  If the recipient accepts the exchange request, invoke the reply(withLocalizableMessageKey:arguments:data:completionHandler:) method. Optionally, pass additional exchange information back to the sender using the `data` parameter.

### Save completed exchanges

When all recipients reply to an exchange request or requests time out, GameKit invokes the player(_:receivedExchangeReplies:forCompletedExchange:for:) method in the current participant’s game instance and the original sender’s game instance.

GameKit passes the exchange object with the status property of GKTurnBasedExchangeStatus.complete and the recipient details (GKTurnBasedExchangeReply objects) in the `replies` parameter. Optionally, present the replies along with their messages and exchange data to the original sender.

If the local player is the current participant, implement the player(_:receivedExchangeReplies:forCompletedExchange:for:) method to resolve and save the exchange data. Also, save completed exchanges before the current participant ends their turn, forfeits the match, or ends the match.

1.  Add your game-specific exchange data to the match data that you save in Game Center and send to participants. For example, add code that transfers items between participants or saves their conversations.

2.  Invoke the saveMergedMatch(_:withResolvedExchanges:completionHandler:) method, passing the current match data, including any exchange data, and the completed exchange objects. This method removes the exchanges from the match’s completedExchanges and exchanges properties.

Only the current participant can invoke the saveMergedMatch(_:withResolvedExchanges:completionHandler:) method, even if the current participant isn’t involved in the exchanges.

### Display exchange results

When the current participant saves completed exchanges with match data, GameKit invokes the player(_:receivedTurnEventFor:didBecomeActive:) method in each participant game instance. Implement this method to present the new match data, including the exchange data. For example, show the items that transfer between participants and recipient reply messages.

### Cancel exchange requests

You can cancel an exchange request anytime before the current participant saves it and the status property becomes GKTurnBasedExchangeStatus.resolved. To cancel an exchange request, use the `GKTurnBasedExchange` cancel(withLocalizableMessageKey:arguments:completionHandler:) method. Pass a localizable message that GameKit displays in a notification if the recipient isn’t running your game or it’s in the background.

```
try await exchange.cancel(withLocalizableMessageKey: "I'm canceling the exchange request.", arguments: [])
```

To update the gameplay interface and display the message when a participant cancels an exchange request, implement the player(_:receivedExchangeCancellation:for:) protocol method.

## See Also

### Turn-based games

Creating turn-based games

Develop games where multiple players take turns and can exchange data while waiting for their turn.

Starting turn-based matches and passing turns between players

Let Game Center store and forward match data between players in a turn-based game.

Sending messages to players in turn-based games

Notify players of match events by sending messages and game data.

class GKTurnBasedMatchmakerViewController

An interface that allows a player to invite other players to a turn-based match and automatch to fill any empty slots.

class GKTurnBasedMatch

An object that encapsulates the match data for games where players take turns.

class GKTurnBasedParticipant

A participant in a turn-based match.

protocol GKTurnBasedEventListener

The protocol that handles turn-based and data-exchange events between participants in a match.

class GKTurnBasedExchange

Exchange request information that participants send in a turn-based match.

class GKTurnBasedExchangeReply

Details about a recipient’s response to an exchange request.

GKGameCenterBadgingDisabled

A Boolean value indicating whether GameKit can add badges to a turn-based game icon.

