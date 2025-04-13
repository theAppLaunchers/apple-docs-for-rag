

- Force Feedback
- FFEFFECT
-  rglDirection 

Instance Property

# rglDirection

Pointer to a LONG array (of **cAxes** elements) containing either Cartesian coordinates, polar coordinates, or spherical coordinates.

Mac Catalyst 13.0+macOS 10.2+

``` source
var rglDirection: LPLONG!
```

## Discussion

The flags FFEFF_CARTESIAN, FFEFF_POLAR, and FFEFF_SPHERICAL determine the semantics of the values in the array.

If Cartesian, each value in rglDirection is associated with the corresponding axis in rgdwAxes.

If polar, the angle is measured in hundredths of degrees from the (0, -1) direction, rotated in the direction of (1, 0). This usually means that north is away from the user, and east is to the user’s right. The last element is not used.

If spherical, the first angle is measured in hundredths of a degree from the (1, 0) direction, rotated in the direction of (0, 1). The second angle (if the number of axes is three or more) is measured in hundredths of a degree toward (0, 0, 1). The third angle (if the number of axes is four or more) is measured in hundredths of a degree toward (0, 0, 0, 1), and so on. The last element is not used.

Note: The rglDirection array must contain cAxes entries, even if polar or spherical coordinates are given. In these cases, the last element in the rglDirection array is reserved for future use and must be 0

## See Also

### Instance Properties

var cAxes: DWORD

Number of axes involved in the effect.

var cbTypeSpecificParams: DWORD

Number of bytes of additional type-specific parameters for the corresponding effect type.

var dwDuration: DWORD

The total duration of the effect, in microseconds. If this value is FF_INFINITE, the effect has infinite duration. If an envelope has been applied to the effect, the attack is applied, followed by an infinite sustain.

var dwFlags: DWORD

Flags associated with an effect.

var dwGain: DWORD

The gain to be applied to the effect, in the range from 0 through 10,000. The gain is a scaling factor applied to all magnitudes of the effect and its envelope.

var dwSamplePeriod: DWORD

The period at which the device should play back the effect, in microseconds.

var dwSize: DWORD

Size, in bytes, of this structure. This member must be initialized before the structure is used.

var dwStartDelay: DWORD

Time (in microseconds) that the device should wait after a FFEffectStart call before playing the effect. If this value is 0, effect playback begins immediately.

var dwTriggerButton: DWORD

The identifier or offset of the button to be used to trigger playback of the effect. The FFJOFS\_\* flags must be used to specify the value. If this member is set to FFEB_NOTRIGGER, no trigger button is associated with the effect.

var dwTriggerRepeatInterval: DWORD

The interval, in microseconds, between the end of one playback and the start of the next when the effect is triggered by a button press and the button is held down. Setting this value to FF_INFINITE suppresses repetition.

var lpEnvelope: PFFENVELOPE!

Optional pointer to a FFENVELOPE structure that describes the envelope to be used by this effect. Not all effect types use envelopes. If no envelope is to be applied, the member should be set to NULL.

var lpvTypeSpecificParams: UnsafeMutableRawPointer!

A pointer to type-specific parameters, or NULL if there are no type-specific parameters.

var rgdwAxes: LPDWORD!

Pointer to a DWORD array (of **cAxes** elements) containing identifiers or offsets identifying the axes to which the effect is to be applied.

