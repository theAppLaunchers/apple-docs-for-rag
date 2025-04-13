

- Core Audio Types
-  kAudioChannelLayoutTag_Quadraphonic 

Global Variable

# kAudioChannelLayoutTag_Quadraphonic

A quadraphonic audio layout.

iOS 2.0+iPadOS 2.0+macOS 10.2+tvOS 9.0+visionOS 1.0+watchOS 3.0+

``` source
var kAudioChannelLayoutTag_Quadraphonic: AudioChannelLayoutTag { get }
```

## Discussion

Quadraphonic recordings use a 90° loudspeaker separation layout. Your channels must be laid out in the following order:

- Left front

- Right front

- Left surround

- Right surround

## See Also

### General Layouts

var kAudioChannelLayoutTag_UseChannelDescriptions: AudioChannelLayoutTag

An array of audio channel description structures that defines the layout mapping.

var kAudioChannelLayoutTag_UseChannelBitmap: AudioChannelLayoutTag

A bitmap that defines the layout mapping.

var kAudioChannelLayoutTag_Mono: AudioChannelLayoutTag

A standard monophonic stream.

var kAudioChannelLayoutTag_Stereo: AudioChannelLayoutTag

A standard stereophonic stream.

var kAudioChannelLayoutTag_StereoHeadphones: AudioChannelLayoutTag

A standard stereo stream; headphone playback implied.

var kAudioChannelLayoutTag_MatrixStereo: AudioChannelLayoutTag

A matrix-encoded stereo stream.

var kAudioChannelLayoutTag_MidSide: AudioChannelLayoutTag

A middle and side channel audio layout.

var kAudioChannelLayoutTag_XY: AudioChannelLayoutTag

A coincident, angled microphone pair.

var kAudioChannelLayoutTag_Binaural: AudioChannelLayoutTag

A binaural stereo audio layout.

var kAudioChannelLayoutTag_Ambisonic_B_Format: AudioChannelLayoutTag

An ambisonic B-format audio layout.

var kAudioChannelLayoutTag_Pentagonal: AudioChannelLayoutTag

A pentalgonal audio layout.

var kAudioChannelLayoutTag_Hexagonal: AudioChannelLayoutTag

A hexagonal audio layout.

var kAudioChannelLayoutTag_Octagonal: AudioChannelLayoutTag

An octagonal audio layout.

var kAudioChannelLayoutTag_Cube: AudioChannelLayoutTag

A cubic audio layout.

