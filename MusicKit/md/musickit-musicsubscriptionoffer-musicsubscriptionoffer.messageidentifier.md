

- MusicKit
- MusicSubscriptionOffer
-  MusicSubscriptionOffer.MessageIdentifier 

Structure

# MusicSubscriptionOffer.MessageIdentifier

An identifier for the main message that the subscription offer sheet presents to the user.

MusicKitSwiftUIiOS 15.0+iPadOS 15.0+Mac Catalyst 15.0+macOS 12.0+

``` source
struct MessageIdentifier
```

## Topics

### Initializers

init(String)

Creates a message identifier with the specified raw value.

init(rawValue: String)

Creates a message identifier with the specified raw value.

### Instance Properties

let rawValue: String

The corresponding value of the raw type.

### Type Aliases

typealias RawValue

The raw type that can be used to represent all values of the conforming type.

### Type Properties

static let addMusic: MusicSubscriptionOffer.MessageIdentifier

An identifier for the message that invites the user to add music to their library by subscribing to Apple Music.

static let join: MusicSubscriptionOffer.MessageIdentifier

An identifier for the message that invites the user to join Apple Music.

static let playMusic: MusicSubscriptionOffer.MessageIdentifier

An identifier for the message that invites the user to play music by subscribing to Apple Music.

### Default Implementations

CustomStringConvertible Implementations

Equatable Implementations

RawRepresentable Implementations

## Relationships

### Conforms To

- Copyable
- CustomStringConvertible
- Equatable
- Hashable
- RawRepresentable
- Sendable

