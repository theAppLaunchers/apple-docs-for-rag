

- Core Media
-  CMSampleBufferCreate(allocator:dataBuffer:dataReady:makeDataReadyCallback:refcon:formatDescription:sampleCount:sampleTimingEntryCount:sampleTimingArray:sampleSizeEntryCount:sampleSizeArray:sampleBufferOut:) 

Function

# CMSampleBufferCreate(allocator:dataBuffer:dataReady:makeDataReadyCallback:refcon:formatDescription:sampleCount:sampleTimingEntryCount:sampleTimingArray:sampleSizeEntryCount:sampleSizeArray:sampleBufferOut:)

Creates a sample buffer with a callback to make the data ready for use.

iOS 4.0+iPadOS 4.0+Mac Catalyst 13.1+macOS 10.7+tvOS 9.0+visionOS 1.0+watchOS 6.0+

``` source
func CMSampleBufferCreate(
    allocator: CFAllocator?,
    dataBuffer: CMBlockBuffer?,
    dataReady: Bool,
    makeDataReadyCallback: CMSampleBufferMakeDataReadyCallback?,
    refcon makeDataReadyRefcon: UnsafeMutableRawPointer?,
    formatDescription: CMFormatDescription?,
    sampleCount numSamples: CMItemCount,
    sampleTimingEntryCount numSampleTimingEntries: CMItemCount,
    sampleTimingArray: UnsafePointer?,
    sampleSizeEntryCount numSampleSizeEntries: CMItemCount,
    sampleSizeArray: UnsafePointer?,
    sampleBufferOut: UnsafeMutablePointer
) -> OSStatus
```

## Parameters 

`allocator`  

The allocator to use for allocating the `CMSampleBuffer` object. Pass `kCFAllocatorDefault` to use the default allocator.

`dataBuffer`  

`CMBlockBuffer` for the media data. This can be `NULL`, a `CMBlockBuffer` with no backing memory, a `CMBlockBuffer` with backing memory but no data yet, or a `CMBlockBuffer` that already contains the media data. If `CMBlockBuffer` contains the media data, `dataReady` should be `true`. The Boolean `dataReady` should also be `true` if the `dataBuffer` is `Null` and `numSamples` is 0.

`dataReady`  

Indicates whether or not the block buffer already contains the media data.

`makeDataReadyCallback`  

Callback that `CMSampleBufferMakeDataReady` should call to make the data ready. Can be `NULL`.

`makeDataReadyRefcon`  

Refcon `CMSampleBufferMakeDataReady` should pass to the callback.

`formatDescription`  

A description of the media data’s format. Can be `NULL`.

`numSamples`  

Number of samples in the `CMSampleBuffer`. Can be zero.

`numSampleTimingEntries`  

Number of entries in `sampleTimingArray`. Must be 0, 1, or `numSamples`.

`sampleTimingArray`  

Array of `CMSampleTimingInfo` structs, one struct per sample. If all samples have the same duration and are in presentation order, you can pass a single `CMSampleTimingInfo` struct with duration set to the duration of one sample, `presentationTimeStamp` set to the presentation time of the numerically earliest sample, and `decodeTimeStamp` set to `kCMTimeInvalid`. Behavior is undefined if samples in a `CMSampleBuffer` (or even in multiple buffers in the same stream) have the same `presentationTimeStamp`. Can be `NULL`.

`numSampleSizeEntries`  

Number of entries in `sampleSizeArray`. Must be 0, 1, or `numSamples`.

`sampleSizeArray`  

Array of size entries, one entry per sample. If all samples have the same size, you can pass a single size entry containing the size of one sample. Can be `NULL`. Must be `NULL` if the samples are non-contiguous in the buffer (for example, non-interleaved audio, where the channel values for a single sample are scattered through the buffer).

`sampleBufferOut`  

On output, points to the newly created `CMSampleBuffer`.

## Return Value

A result code. See Sample Buffer Error Codes.

## Discussion

Array parameters (`sampleSizeArray`, `sampleTimingArray`) should have only one element if that same element applies to all samples. All parameters are copied. On return, the caller can release them, free them or reuse them. On return, the caller owns the returned `CMSampleBuffer`, and must release it when done with it.

Example of usage for in-display-order video frames:

- dataBuffer: contains 7 Motion JPEG frames

- dataFormatDescription: describes Motion JPEG video

- dataFormatDescription: describes Motion JPEG video

- numSamples: 7

- numSampleTimingEntries: 1

- sampleTimingArray: one entry = {duration = 1001/30000, presentationTimeStamp = 0/30000, decodeTimeStamp = invalid }

- numSampleSizeEntries: 7

- sampleSizeArray: \[105840, 104456, 103464, 116460, 100412, 94808, 120400\]

Example of usage for video frames in out-of-display-order :

- dataBuffer: contains 6 H.264 frames in decode order (P2,B0,B1,I5,B3,B4)

- dataFormatDescription: describes H.264 video

- numSamples: 6

- numSampleTimingEntries: 6

- sampleTimingArray: 6 entries = {

- {duration = 1001/30000, presentationTimeStamp = 12012/30000, decodeTimeStamp = 10010/30000},

- {duration = 1001/30000, presentationTimeStamp = 10010/30000, decodeTimeStamp = 11011/30000},

- {duration = 1001/30000, presentationTimeStamp = 11011/30000, decodeTimeStamp = 12012/30000},

- {duration = 1001/30000, presentationTimeStamp = 15015/30000, decodeTimeStamp = 13013/30000},

- {duration = 1001/30000, presentationTimeStamp = 13013/30000, decodeTimeStamp = 14014/30000},

- {duration = 1001/30000, presentationTimeStamp = 13013/30000, decodeTimeStamp = 14014/30000}}

- numSampleSizeEntries: 6

- sampleSizeArray: \[10580, 1234, 1364, 75660, 1012, 988\]

Example of usage for compressed audio:

- dataBuffer: contains 24 compressed AAC packets

- dataFormatDescription: describes 44.1kHz AAC audio

- numSamples: 24

- numSampleTimingEntries: 1

- sampleTimingArray: one entry = {{duration = 1024/44100, presentationTimeStamp = 0/44100, decodeTimeStamp = invalid }}

- numSampleSizeEntries: 24

- sampleSizeArray:\[191, 183, 208, 213, 202, 206, 209, 206, 204, 192, 202, 277, 282, 240, 209, 194, 193, 197, 196, 198, 168, 199, 171, 194\]

Example of usage for uncompressed interleaved audio:

- dataBuffer: contains 24000 uncompressed interleaved stereo frames, each containing 2 Float32s =

- {{L,R},

- {L,R},

- {L,R}, …}

- dataFormatDescription: describes 48kHz Float32 interleaved audio

- numSamples: 24000

- numSampleTimingEntries: 1

- sampleTimingArray: one entry = {{duration = 1/48000, presentationTimeStamp = 0/48000, decodeTimeStamp = invalid }}

- numSampleSizeEntries: 1

- sampleSizeArray: {8}

Example of usage for uncompressed non-interleaved audio:

- dataBuffer: contains 24000 uncompressed non-interleaved stereo frames, each containing 2 (non-contiguous) Float32s =

- {{L,L,L,L,L,…},

- {R,R,R,R,R,…}}

- dataFormatDescription: describes 48kHz Float32 non-interleaved audio

- numSamples: 24000

- numSampleTimingEntries: 1

- sampleTimingArray: one entry = {duration = 1/48000, presentationTimeStamp = 0/48000, decodeTimeStamp = invalid }

- numSampleSizeEntries: 0

- sampleSizeArray: `NULL` (because the samples aren’t contiguous)

## Topics

### Callbacks

typealias CMSampleBufferMakeDataReadyCallback

Client callback called by CMSampleBufferMakeDataReady(_:).

## See Also

### Creating Sample Buffers

func CMSampleBufferCreateReady(allocator: CFAllocator?, dataBuffer: CMBlockBuffer?, formatDescription: CMFormatDescription?, sampleCount: CMItemCount, sampleTimingEntryCount: CMItemCount, sampleTimingArray: UnsafePointer&lt;CMSampleTimingInfo>?, sampleSizeEntryCount: CMItemCount, sampleSizeArray: UnsafePointer&lt;Int>?, sampleBufferOut: UnsafeMutablePointer&lt;CMSampleBuffer?>) -> OSStatus

Creates a sample buffer with media data.

func CMSampleBufferCreateReadyWithImageBuffer(allocator: CFAllocator?, imageBuffer: CVImageBuffer, formatDescription: CMVideoFormatDescription, sampleTiming: UnsafePointer&lt;CMSampleTimingInfo>, sampleBufferOut: UnsafeMutablePointer&lt;CMSampleBuffer?>) -> OSStatus

Creates a sample buffer with image data.

func CMAudioSampleBufferCreateReadyWithPacketDescriptions(allocator: CFAllocator?, dataBuffer: CMBlockBuffer, formatDescription: CMFormatDescription, sampleCount: CMItemCount, presentationTimeStamp: CMTime, packetDescriptions: UnsafePointer&lt;AudioStreamPacketDescription>?, sampleBufferOut: UnsafeMutablePointer&lt;CMSampleBuffer?>) -> OSStatus

Creates a sample buffer with packet descriptions.

func CMSampleBufferCreateWithMakeDataReadyHandler(CFAllocator?, CMBlockBuffer?, Bool, CMFormatDescription?, CMItemCount, CMItemCount, UnsafePointer&lt;CMSampleTimingInfo>?, CMItemCount, UnsafePointer&lt;Int>?, UnsafeMutablePointer&lt;CMSampleBuffer?>, CMSampleBufferMakeDataReadyHandler?) -> OSStatus

Creates a sample buffer with a handler to make the data ready for use.

func CMSampleBufferCreateForImageBufferWithMakeDataReadyHandler(CFAllocator?, CVImageBuffer, Bool, CMVideoFormatDescription, UnsafePointer&lt;CMSampleTimingInfo>, UnsafeMutablePointer&lt;CMSampleBuffer?>, CMSampleBufferMakeDataReadyHandler?) -> OSStatus

Creates a sample buffer with an image buffer and a handler to make the data ready for use.

func CMAudioSampleBufferCreateWithPacketDescriptionsAndMakeDataReadyHandler(CFAllocator?, CMBlockBuffer?, Bool, CMFormatDescription, CMItemCount, CMTime, UnsafePointer&lt;AudioStreamPacketDescription>?, UnsafeMutablePointer&lt;CMSampleBuffer?>, CMSampleBufferMakeDataReadyHandler?) -> OSStatus

Creates a sample buffer with packet descriptions and a handler to make the data ready for use.

func CMSampleBufferCreateForImageBuffer(allocator: CFAllocator?, imageBuffer: CVImageBuffer, dataReady: Bool, makeDataReadyCallback: CMSampleBufferMakeDataReadyCallback?, refcon: UnsafeMutableRawPointer?, formatDescription: CMVideoFormatDescription, sampleTiming: UnsafePointer&lt;CMSampleTimingInfo>, sampleBufferOut: UnsafeMutablePointer&lt;CMSampleBuffer?>) -> OSStatus

Creates a sample buffer with an image buffer and a callback to make the data ready for use.

func CMAudioSampleBufferCreateWithPacketDescriptions(allocator: CFAllocator?, dataBuffer: CMBlockBuffer?, dataReady: Bool, makeDataReadyCallback: CMSampleBufferMakeDataReadyCallback?, refcon: UnsafeMutableRawPointer?, formatDescription: CMFormatDescription, sampleCount: CMItemCount, presentationTimeStamp: CMTime, packetDescriptions: UnsafePointer&lt;AudioStreamPacketDescription>?, sampleBufferOut: UnsafeMutablePointer&lt;CMSampleBuffer?>) -> OSStatus

Creates a sample buffer with packet descriptions and a callback to make the data ready for use.

