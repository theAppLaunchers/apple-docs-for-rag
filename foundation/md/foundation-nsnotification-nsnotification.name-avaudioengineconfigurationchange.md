

- Foundation
- NSNotification
- NSNotification.Name
-  AVAudioEngineConfigurationChange 

Type Property

# AVAudioEngineConfigurationChange

A notification the framework posts when the audio engine configuration changes.

iOS 8.0+iPadOS 8.0+Mac Catalyst 13.1+macOS 10.10+tvOS 9.0+visionOS 1.0+watchOS 2.0+

``` source
static let AVAudioEngineConfigurationChange: NSNotification.Name
```

## Discussion

When the audio engine’s I/O unit observes a change to the audio input or output hardware’s channel count or sample rate, the audio engine stops, uninitializes itself, and issues this notification. The nodes remain in an attached and connected state with the previously set formats. The app must reestablish connections if the connection formats need to change.

Note

Don’t deallocate the engine from within the client’s notification handler. The callback happens on an internal dispatch queue and can deadlock while trying to tear down the engine synchronously.

## See Also

### AVFAudio

static let AVAudioUnitComponentTagsDidChange: NSNotification.Name

A notification that indicates when component tags change.

class let interruptionNotification: NSNotification.Name

A notification the system posts when an audio interruption occurs.

class let mediaServicesWereLostNotification: NSNotification.Name

A notification the system posts when it terminates the media server.

class let mediaServicesWereResetNotification: NSNotification.Name

A notification the system posts when the media server restarts.

class let routeChangeNotification: NSNotification.Name

A notification the system posts when its audio route changes.

class let silenceSecondaryAudioHintNotification: NSNotification.Name

A notification the system posts when the primary audio from other apps starts and stops.

