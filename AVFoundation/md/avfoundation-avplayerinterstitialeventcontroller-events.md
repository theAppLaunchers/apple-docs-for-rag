

- AVFoundation
- AVPlayerInterstitialEventController
-  events 

Instance Property

# events

The current schedule of interstitial events.

iOS 15.0+iPadOS 15.0+Mac Catalyst 15.0+macOS 12.0+tvOS 15.0+visionOS 1.0+watchOS 8.0+

``` source
var events: [AVPlayerInterstitialEvent]! { get set }
```

## Discussion

Setting this property to a non-`nil` value cancels and overrides all previously scheduled future interstitial events, including those that the primary item’s content specifies, such as directives carried by an HLS media playlists. Setting the value to an empty array clears the schedule or, if the server specifies interstitial events, reverts it to the server’s schedule.

Note

An event controller copies the events that you set for this value. Making subsequent changes to the events doesn’t impact the event schedule.

Changing the value of this property doesn’t impact currently playing interstitials. To cancel the current event, call cancelCurrentEvent(withResumptionOffset:).

Important

The system raises an exception if you schedule an event that doesn’t provide the required data, such as one lacking a valid primaryItem value, or a valid date or time.

If you schedule interstitial events with dates that coincide either with the date of another scheduled interstitial event, or with a date range in the primary content’s timeline that the resumption offset of another scheduled interstitial event omits, the primary content remains suspended until all coinciding interstitial events complete. The system orders their playback according to their position in the array. The effective resumption offset is the sum of the resumption offsets of the coinciding events.

Note

Summing a numeric CMTime and an indefinite time results in an indefinite value.

## See Also

### Configuring the Event Schedule

func cancelCurrentEvent(withResumptionOffset: CMTime)

Cancels the playback of all currently playing and scheduled interstitial events, and resumes playback of primary content.

