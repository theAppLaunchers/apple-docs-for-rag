Framework

# ShazamKit

Find information about a specific audio recording when a segment of it’s part of captured sound in the Shazam catalog or your custom catalog.

iOS 15.0+iPadOS 15.0+Mac Catalyst 15.0+macOS 12.0+tvOS 15.0+visionOS 1.0+watchOS 8.0+

## [Overview](/documentation/ShazamKit#overview)

ShazamKit uses the unique acoustic _signature_ of an audio recording to find a match. This signature captures the time-frequency distribution of the audio signal energy, and is much smaller than the original audio. It’s also a one-way conversion, so it’s not possible to convert the signature back to the recording.

ShazamKit generates a _reference signature_ for each searchable full audio recording. A _catalog_ stores the reference signatures and their associated metadata, or _media items_.

Searching for a match compares a _query signature_, which ShazamKit generates for captured audio, with the reference signatures in the catalog. Matches occur when the query signature sufficiently matches a part of a reference signature. Matches can occur even when the captured audio is noisy, such as with a partial recording of background music playing in a restaurant.

The figure below illustrates matching a query signature with the reference signature in the catalog. The information for a match includes the timecode in the reference recording that matches the start of the query.

![A spectrogram that shows the signature match for a query signature at a specific point in time in a reference signature.](https://docs-assets.developer.apple.com/published/685947e963164829076ac3ec0fe3bbc1/media-3807548%402x.png)

For example, the Shazam app converts the sound stream from a device’s microphone into a query signature and searches for a match in the Shazam music catalog. The match includes the metadata for the reference signature, such as the song title, artist name, and other details.

You can create a custom catalog with your own reference signatures and their associated metadata. For example, the catalog for a virtual learning app might contain reference signatures for teaching videos, and the associated metadata that includes the timecodes for questions. Using ShazamKit, the app identifies the current question by the timecode for the match, and can offer choices for a possible answer. If the student skips forward or backward in the video, the app updates according to the sound of what the student is watching.

## [Topics](/documentation/ShazamKit#topics)

### [Match audio](/documentation/ShazamKit#Match-audio)

```swift
```swift
```swift
```swift
class SHSession
```
```

An object that matches a specific audio recording when a segment of that recording is part of captured sound in the Shazam catalog or your custom catalog.
```
```swift
```swift
```swift
class SHManagedSession
```
```

An object that records and matches a recording with captured sound in the Shazam catalog or your custom catalog.
```
```swift
```swift
```swift
protocol SHSessionDelegate
```
```

Methods that the session calls with the result of a match request.
```
```swift
```swift
```swift
class SHMatch
```
```

An object that represents the catalog media items that match a query.
```
```swift
```swift
```swift
class SHMatchedMediaItem
```
```

An object that represents the metadata for a matched reference signature.
```
```swift
```swift
```swift
class SHMediaItem
```
```

An object that represents the metadata for a reference signature.
```
```

### [Create a signature from audio](/documentation/ShazamKit#Create-a-signature-from-audio)

```swift
```swift
```swift
```swift
class SHSignature
```
```

An object that contains the opaque data and other information for a signature.
```
```swift
```swift
```swift
class SHSignatureGenerator
```
```

An object for converting audio data into a signature.
```
```

### [Create a custom audio catalog](/documentation/ShazamKit#Create-a-custom-audio-catalog)

[

Building a Custom Catalog and Matching Audio](/documentation/shazamkit/building-a-custom-catalog-and-matching-audio)

Display lesson content that’s synchronized to a learning video by matching the audio to a custom reference signature and associated metadata.

[

ShazamKit Dance Finder with Managed Session](/documentation/shazamkit/shazamkit-dance-finder-with-managed-session)

Find a video of dance moves for a specific song by matching the audio to a custom catalog, and show a history of recognized songs.

```swift
```swift
```swift
class SHCustomCatalog
```
```

An object for storing the reference signatures for custom audio recordings and their associated metadata.
```
```swift
```swift
```swift
class SHCatalog
```
```

An abstract base class for storing reference signatures and their associated metadata.
```

### [Update the user’s Shazam library](/documentation/ShazamKit#Update-the-users-Shazam-library)

```swift
```swift
```swift
```swift
class SHLibrary
```
```

An object that represents a user’s synced Shazam library.
```
```swift
```swift
```swift
class SHMediaLibrary
```
```

An object that represents the user’s Shazam library.

Deprecated
```
```

### [Shazam errors](/documentation/ShazamKit#Shazam-errors)

```swift
```swift
```swift
```swift
struct SHError
```
```

An error type that you create, or the system creates, to indicate problems with a catalog, match attempt, or signature, or when saving to a user’s Shazam library.
```
```

### [Reference](/documentation/ShazamKit#Reference)

[

API Reference

ShazamKit Enumerations](/documentation/shazamkit/shazamkit-enumerations)

[

API Reference

ShazamKit Constants](/documentation/shazamkit/shazamkit-constants)