

- Audio Toolbox
- AUAudioUnit
-  latency 

Instance Property

# latency

The audio unit’s processing latency, in seconds.

iOS 9.0+iPadOS 9.0+Mac Catalyst 13.1+macOS 10.11+tvOS 9.0+visionOS 1.0+

``` source
var latency: TimeInterval { get }
```

## Discussion

This property reflects the delay between when an impulse arrives in the input stream vs. output stream. This should reflect the delay due to signal processing (e.g. FFTs), not as an effect (e.g. reverberation).

Note that a latency that varies with parameter settings, including bypass, is generally not useful to hosts. A host is usually only prepared to add delays before starting to render and those delays need to be fixed. A variable delay would introduce artifacts even if the host could track it. If an algorithm has a variable latency, it should be adjusted upwards to some fixed latency within the audio unit. If for some reason this is not possible, then latency could be regarded as an unavoidable consequence of the algorithm and left unreported (i.e. a value of `0`).

This version 3 property is bridged to the version 2 `kAudioUnitProperty_Latency` API.

## See Also

### Optimizing Performance

var tailTime: TimeInterval

The audio unit’s tail time, in seconds.

var renderQuality: Int

Provides a trade-off between rendering quality and CPU load.

var shouldBypassEffect: Bool

Determines whether an effect should route input directly to output, without any processing.

var canProcessInPlace: Bool

Determines whether an audio unit can process in place.

var isRenderingOffline: Bool

Communicates to an audio unit that it is rendering offline.

