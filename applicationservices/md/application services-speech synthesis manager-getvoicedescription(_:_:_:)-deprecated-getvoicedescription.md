

- Application Services
- Speech Synthesis Manager
-  GetVoiceDescription(\_:\_:\_:) Deprecated

Function

# GetVoiceDescription(\_:\_:\_:)

Gets a description of a voice by using the `GetVoiceDescription` function.

macOS 10.0–13.0Deprecated

``` source
func GetVoiceDescription(
    _ voice: UnsafePointer?,
    _ info: UnsafeMutablePointer?,
    _ infoLength: Int
) -> OSErr
```

## Parameters 

`voice`  

A pointer to the voice specification structure identifying the voice to be described, or `NULL` to obtain a description of the system default voice.

`info`  

A pointer to a voice description structure. If this parameter is `NULL`, the function does not fill in the fields of the voice description structure; instead, it simply determines whether the `voice` parameter specifies an available voice and, if not, returns a `voiceNotFound` error.

`infoLength`  

The length, in bytes, of the voice description structure. In the current version of the Speech Synthesis Manager, the voice description structure contains 362 bytes. However, you should always use the `SizeOf` function to determine the length of this structure.

## Return Value

A resultcode. See Result Codes.

## Discussion

The `GetVoiceDescription` functionfills out the voice description structure pointed to by the `info` parameterwith the correct information for the voice specified by the `voice` parameter. Itfills in the `length` fieldof the voice description structure with the number of bytes actuallycopied. This value will always be less than or equal to the valuethat your application passes in `infoLength` beforecalling `GetVoiceDescription`.This scheme allows applications targeted for the current versionof the Speech Synthesis Manager to work on future versions thatmight have longer voice description structures; it also allows youto write code for future versions of the Speech Synthesis Managerthat will also run on computers that support only the current version.

If the voice specification structure does not identify anavailable voice, `GetVoiceDescription` returnsa `voiceNotFound` error.

## See Also

### Getting Information About Voices

func CountVoices(UnsafeMutablePointer&lt;Int16>) -> OSErr

Determines how many voices are available.

Deprecated

func GetIndVoice(Int16, UnsafeMutablePointer&lt;VoiceSpec>) -> OSErr

Gets a voice specification structure for a voice bypassing an index to the `GetIndVoice` function.

Deprecated

func GetVoiceInfo(UnsafePointer&lt;VoiceSpec>?, OSType, UnsafeMutableRawPointer) -> OSErr

Gets the same information about a voice that the `GetVoiceDescription` function provides,or to determine in which file and resource a voice is stored.

Deprecated

func MakeVoiceSpec(OSType, OSType, UnsafeMutablePointer&lt;VoiceSpec>) -> OSErr

Sets the fields of a voice specification structure.

Deprecated

