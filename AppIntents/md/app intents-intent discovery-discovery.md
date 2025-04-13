

- App Intents
-  Intent discovery 

API Collection

# Intent discovery

Donate your app’s intents to the system to help it identify trends and predict future behaviors.

## Overview

Make your intents more discoverable to people by donating them to the system. When someone performs an action in your app, donate an intent that corresponds to that action. The system uses the information you provide to predict actions someone might take in the future. For example, if someone requests the weather from your app each morning, the system might proactively offer the corresponding app intent at the same time each day.

Donate intents only when someone uses your app’s interface directly. You don’t need to donate intents associated with Siri or interactions with the Shortcuts app because the system donates them automatically. You can also delete donations when someone cancels or reverses a previously executed action, or when the action is no longer relevant.

## Topics

### Donation management

struct IntentDonationManager

A type you use to donate intents to the system, or delete intents when they become irrelevant.

struct IntentDonationIdentifier

An opaque type that identifies a specific donation to the system.

struct IntentDonationMatchingPredicate

The match conditions that identify a set of previously donated app intents.

### Intent predictions

protocol PredictableIntent

An interface that allows the system to suggest the app intent to someone in the future using predictions you provide.

struct IntentPrediction

A prediction for a specific app intent that the system might display to someone when it’s relevant.

### Intent relevancy

struct RelevantIntent

A type that specifies an intent and its relevance to the user.

class RelevantIntentManager

A type that saves relevant intents.

struct RelevantContext

A type that specifies conditions for relevance.

## See Also

### Actions

App intents

Define the custom actions your app exposes to the system, and incorporate support for existing SiriKit intents.

App Shortcuts

Integrate your app’s intents and entities with the Shortcuts app, Siri, Spotlight, and the Action button on supported iPhone and Apple Watch models.

