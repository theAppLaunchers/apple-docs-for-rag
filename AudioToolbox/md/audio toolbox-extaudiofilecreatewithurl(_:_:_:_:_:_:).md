

- Audio Toolbox
-  ExtAudioFileCreateWithURL(\_:\_:\_:\_:\_:\_:) 

Function

# ExtAudioFileCreateWithURL(\_:\_:\_:\_:\_:\_:)

Creates a new audio file and associates it with a new extended audio file object.

iOS 2.1+iPadOS 2.1+Mac Catalyst 13.1+macOS 10.5+tvOS 9.0+visionOS 1.0+

``` source
func ExtAudioFileCreateWithURL(
    _ inURL: CFURL,
    _ inFileType: AudioFileTypeID,
    _ inStreamDesc: UnsafePointer,
    _ inChannelLayout: UnsafePointer?,
    _ inFlags: UInt32,
    _ outExtAudioFile: UnsafeMutablePointer
) -> OSStatus
```

## Parameters 

`inURL`  

The URL of the new audio file.

`inFileType`  

The type of file to create, specified as a constant from the AudioFileTypeID enumeration.

`inStreamDesc`  

The format of the audio data to be written to the file.

`inChannelLayout`  

The channel layout of the audio data. If non-null, this must be consistent with the number of channels specified by the `inStreamDesc` parameter.

`inFlags`  

Flags for creating or opening the file. If the eraseFile flag is set, it erases an existing file. If the flag is not set, the function fails fails if the URL points to an existing file.

`outExtAudioFile`  

On output, a newly allocated extended audio file object.

## Return Value

A result code.

## Discussion

If the file to be created is in a compressed format, you may set the sample rate in the `inStreamDesc` parameter to `0`. In all cases, the extended file object’s encoding converter may produce audio at a different sample rate than the source. The file will be created with the audio format produced by the encoder.

## See Also

### Managing Extended Audio File Objects

func ExtAudioFileDispose(ExtAudioFileRef) -> OSStatus

Disposes of an extended audio file object and closes the associated file.

func ExtAudioFileOpenURL(CFURL, UnsafeMutablePointer&lt;ExtAudioFileRef?>) -> OSStatus

Opens an existing audio file for reading, and associates it with a new extended audio file object.

func ExtAudioFileWrapAudioFileID(AudioFileID, Bool, UnsafeMutablePointer&lt;ExtAudioFileRef?>) -> OSStatus

Wraps an audio file object in an extended audio file object.

