Collection

*   [Media Accessibility](/documentation/mediaaccessibility)
*   Music Haptics

API Collection

# Music Haptics

Play haptic tracks along with known music tracks.

## [Overview](/documentation/MediaAccessibility/music-haptics#Overview)

Music Haptics is an accessibility feature that allows a person to indicate that they want to play haptic tracks along with known music tracks. This feature allows people who are deaf or hard of hearing to enjoy music through tactile feedback. A person can turn on this feature in Settings > Accessibility > Music Haptics. If you play music in your app, you can support haptic feedback for known songs.

### [Support Music Haptics](/documentation/MediaAccessibility/music-haptics#Support-Music-Haptics)

To support Music Haptics in your app:

*   Add the [`MusicHapticsSupported`](/documentation/BundleResources/Information-Property-List/MusicHapticsSupported) key to your app’s `Info.plist` and set its value to `YES`.
    
*   Check whether Music Haptics is on using [`isActive`](/documentation/mediaaccessibility/mamusichapticsmanager/isactive) on the [`shared`](/documentation/mediaaccessibility/mamusichapticsmanager/shared) instance of [`MAMusicHapticsManager`](/documentation/mediaaccessibility/mamusichapticsmanager).
    
*   Register for the [`activeStatusDidChangeNotification`](/documentation/mediaaccessibility/mamusichapticsmanager/activestatusdidchangenotification) notification to listen for changes in the Music Haptics setting.
    
*   Supply a known song’s International Standard Recording Code (ISRC) as part of the [`nowPlayingInfo`](/documentation/MediaPlayer/MPNowPlayingInfoCenter/nowPlayingInfo) dictionary of [`MPNowPlayingInfoCenter`](/documentation/MediaPlayer/MPNowPlayingInfoCenter), using the key [`MPNowPlayingInfoPropertyInternationalStandardRecordingCode`](/documentation/MediaPlayer/MPNowPlayingInfoPropertyInternationalStandardRecordingCode). For more information about becoming the Now Playing app, refer to [Becoming a now playable app](/documentation/MediaPlayer/becoming-a-now-playable-app).
    

### [Indicate haptic playback status](/documentation/MediaAccessibility/music-haptics#Indicate-haptic-playback-status)

To indicate the status of haptic playback for Music Haptics, you can use the following symbols:

Symbol name

Status

API

`"apple.haptics.and.music.note"`

Active

[`isActive`](/documentation/mediaaccessibility/mamusichapticsmanager/isactive) is `true`

`"apple.haptics.and.music.note.slash"`

Paused

[`isActive`](/documentation/mediaaccessibility/mamusichapticsmanager/isactive) is `false`

`"apple.haptics.and.exclamationmark.triangle"`

Unavailable

[`checkHapticTrackAvailabilityForMedia(matchingCode:completionHandler:)`](/documentation/mediaaccessibility/mamusichapticsmanager/checkhaptictrackavailabilityformedia\(matchingcode:completionhandler:\)) is `false`

For more details about using these symbols, refer to the [SF Symbols](https://developer.apple.com/sf-symbols/) app.

## [Topics](/documentation/MediaAccessibility/music-haptics#topics)

### [Music Haptics](/documentation/MediaAccessibility/music-haptics#Music-Haptics)

```swift
```swift
```swift
```swift
class MAMusicHapticsManager
```
```

A class that reports information about the Music Haptics feature.
```
```

## [See Also](/documentation/MediaAccessibility/music-haptics#see-also)

### [Features](/documentation/MediaAccessibility/music-haptics#Features)

[

API Reference

Captions](/documentation/mediaaccessibility/captions)

Coordinate the presentation of closed-captioned data for your app’s media files.

[

API Reference

Flashing lights](/documentation/mediaaccessibility/flashing-lights)

Detect, mitigate, and inform people about flashing lights in media content.