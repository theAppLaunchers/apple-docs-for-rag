

- Audio Toolbox
-  AudioFileGetUserDataSize64(\_:\_:\_:\_:) 

Function

# AudioFileGetUserDataSize64(\_:\_:\_:\_:)

Gets the size of a user data item in an audio file.

iOS 17.0+iPadOS 17.0+Mac Catalyst 17.0+macOS 14.0+tvOS 17.0+visionOS 1.0+

``` source
func AudioFileGetUserDataSize64(
    _ inAudioFile: AudioFileID,
    _ inUserDataID: UInt32,
    _ inIndex: UInt32,
    _ outUserDataSize: UnsafeMutablePointer
) -> OSStatus
```

## Parameters 

`inAudioFile`  

The audio file whose user data item size you want.

`inUserDataID`  

The four-character code of the designated user data item.

`inIndex`  

An index of the user data item with the four-character code specified in `inUserDataID` that you want to query.

`outUserDataSize`  

On output, if successful, the size of the user data item.

## Return Value

A result code if there’s an error (see Result Codes) or `noErr` if the operation succeeds.

## Discussion

In this function, *user data* refers to:

- Chunks in AIFF, CAF, and WAVE files

- Resources in Sound Designer II files

- Other types of information in other files

Very large user data chunks, such as the Audio Definition Model (ADM) chunks that movie production uses, can exceed the 32-bit size limit or be prohibitively expensive to allocate large enough memory blocks to read them.

The BW64 format is 64-bit and based on WAVE. Parsing the ADM of a BW64 file with metadata becomes an iterative process that doesn’t require large memory buffers. In the following example, `ADMBuilder` is a type that uses the Builder pattern to parse an ADM document from sequentially provided segments:

```
constexpr size_t CHUNK_BUFFER_SIZE = 16 * 1024;  // Arbitrary, but 16K is the typical page size.
    AudioFileID inputAudioFile;

    // Assume that the system successfully opened the audio file.

    uint64_t chunkSize = 0;
    auto err = AudioFileGetUserDataSize64(inputAudioFile, 'axml', 0, &chunkSize);

    if (err != noErr) {
        if (err == kAudioFileInvalidChunkError) {
            fprintf(stderr, "The input file doesn't appear to have an ADM document attached.\n");
            return EXIT_FAILURE;
        }
        fprintf(stderr, "AudioFileGetUserDataSize64 returned error: %d.\n", (int)err);
        return EXIT_FAILURE;
    }

    printf("ADM is %" PRIu64 " bytes in size.\n", chunkSize);
    ADMBuilder admBuilder;
    std::vector buffer(CHUNK_BUFFER_SIZE);
    uint64_t offset = 0;

    while (offset = chunkSize);
        if (err != noErr) {
            fprintf(stderr, "ADMBuilder::parse returned error: %d.\n", (int)err);
            return EXIT_FAILURE;
        }

        offset += (uint64_t)readSize;
    }

    // Assume that the system reads and uses the audio frames from the file, along
    // with the parsed ADM document, and the system eventually closes the audio file.

    return EXIT_SUCCESS;

```

## See Also

### Working with User Data

func AudioFileCountUserData(AudioFileID, UInt32, UnsafeMutablePointer&lt;UInt32>) -> OSStatus

Gets the number of user data items with a specified ID in a file.

func AudioFileGetUserDataSize(AudioFileID, UInt32, UInt32, UnsafeMutablePointer&lt;UInt32>) -> OSStatus

Gets the size of a user data item in an audio file.

func AudioFileGetUserData(AudioFileID, UInt32, UInt32, UnsafeMutablePointer&lt;UInt32>, UnsafeMutableRawPointer) -> OSStatus

Gets a chunk from an audio file.

func AudioFileGetUserDataAtOffset(AudioFileID, UInt32, UInt32, Int64, UnsafeMutablePointer&lt;UInt32>, UnsafeMutableRawPointer) -> OSStatus

Gets part of the data from a chunk in an audio file.

func AudioFileSetUserData(AudioFileID, UInt32, UInt32, UInt32, UnsafeRawPointer) -> OSStatus

Sets a user data item in an audio file.

func AudioFileRemoveUserData(AudioFileID, UInt32, UInt32) -> OSStatus

Removes a user data item from an audio file.

