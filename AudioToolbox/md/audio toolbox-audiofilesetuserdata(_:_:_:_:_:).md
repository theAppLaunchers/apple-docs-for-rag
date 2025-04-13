

- Audio Toolbox
-  AudioFileSetUserData(\_:\_:\_:\_:\_:) 

Function

# AudioFileSetUserData(\_:\_:\_:\_:\_:)

Sets a user data item in an audio file.

iOS 2.0+iPadOS 2.0+Mac Catalyst 13.1+macOS 10.4+tvOS 9.0+visionOS 1.0+

``` source
func AudioFileSetUserData(
    _ inAudioFile: AudioFileID,
    _ inUserDataID: UInt32,
    _ inIndex: UInt32,
    _ inUserDataSize: UInt32,
    _ inUserData: UnsafeRawPointer
) -> OSStatus
```

## Parameters 

`inAudioFile`  

The audio file that you want to set a user data item in.

`inUserDataID`  

The four-character code for the user data item.

`inIndex`  

An index specifying the user data item you want to set. You use this parameter if the file contains more than one user data item with the four-character code specified in the `inUserDataID` parameter.

`inUserDataSize`  

On input, the size of the data to copy. On output, the size of the bytes copied from the buffer.

`inUserData`  

A pointer to a buffer from which to copy the user data.

## Return Value

A result code if there’s an error (see Result Codes) or `noErr` if the operation succeeds.

## See Also

### Working with User Data

func AudioFileCountUserData(AudioFileID, UInt32, UnsafeMutablePointer&lt;UInt32>) -> OSStatus

Gets the number of user data items with a specified ID in a file.

func AudioFileGetUserDataSize(AudioFileID, UInt32, UInt32, UnsafeMutablePointer&lt;UInt32>) -> OSStatus

Gets the size of a user data item in an audio file.

func AudioFileGetUserDataSize64(AudioFileID, UInt32, UInt32, UnsafeMutablePointer&lt;UInt64>) -> OSStatus

Gets the size of a user data item in an audio file.

func AudioFileGetUserData(AudioFileID, UInt32, UInt32, UnsafeMutablePointer&lt;UInt32>, UnsafeMutableRawPointer) -> OSStatus

Gets a chunk from an audio file.

func AudioFileGetUserDataAtOffset(AudioFileID, UInt32, UInt32, Int64, UnsafeMutablePointer&lt;UInt32>, UnsafeMutableRawPointer) -> OSStatus

Gets part of the data from a chunk in an audio file.

func AudioFileRemoveUserData(AudioFileID, UInt32, UInt32) -> OSStatus

Removes a user data item from an audio file.

