

- AVFoundation
-  AVSampleCursor 

Class

# AVSampleCursor

An object that provides information about the media sample at the cursor’s current position.

iOS 16.0+iPadOS 16.0+Mac Catalyst 16.0+macOS 10.10+tvOS 16.0+visionOS 1.0+watchOS 9.0+

``` source
class AVSampleCursor
```

## Overview

You position a sample cursor at a specific media sample in a sequence of samples contained in a higher-level object, like an AVAssetTrack. You can move it to a new position in that sequence either backwards or forwards, either in decode order or in presentation order. You can also request moving it according to a count of samples or a delta in time.

Use a sample cursor to get information about the media sample such as its duration, timestamps, dependency information, and so on. You can also use them to synchronously to perform I/O in order to load media data of one or more media samples into memory.

## Topics

### Navigating Samples

func step(byDecodeTime: CMTime, wasPinned: UnsafeMutablePointer&lt;ObjCBool>?) -> CMTime

Moves the cursor by a given delta time on the decode timeline.

func step(byPresentationTime: CMTime, wasPinned: UnsafeMutablePointer&lt;ObjCBool>?) -> CMTime

Moves the cursor by a given delta time on the presentation timeline.

func stepInDecodeOrder(byCount: Int64) -> Int64

Moves the cursor a given number of samples in decode order.

func stepInPresentationOrder(byCount: Int64) -> Int64

Moves the cursor a given number of samples in presentation order.

### Getting Timestamps

var decodeTimeStamp: CMTime

The decode timestamp of the sample at the current position of the cursor.

var presentationTimeStamp: CMTime

The presentation timestamp of the sample at the current position of the cursor.

### Getting Sample Information

var currentChunkInfo: AVSampleCursorChunkInfo

A value that provides information about the chunk of samples to which the current sample belongs.

struct AVSampleCursorChunkInfo

A value that provides information about a chunk of media samples.

var currentChunkStorageRange: AVSampleCursorStorageRange

The sample range in the storage container to load together with the current sample as a chunk.

struct AVSampleCursorStorageRange

A structure that indicates the offset and length of storage for a media sample or its chunk.

var currentChunkStorageURL: URL?

The URL of the storage container of the current sample and other samples to load in the same operation as a chunk.

var currentSampleDependencyInfo: AVSampleCursorDependencyInfo

The dependency information that describes relationships between a media sample and other media samples in the same sample sequence.

struct AVSampleCursorDependencyInfo

A value for describing dependencies between a media sample and other media samples in the same sample sequence.

var currentSampleDuration: CMTime

The decode duration of the sample at the cursor’s current position.

var currentSampleIndexInChunk: Int64

The index of the current sample within the chunk to which it belongs.

var currentSampleStorageRange: AVSampleCursorStorageRange

The offset and length of the current sample in the current chunk storage URL.

var currentSampleSyncInfo: AVSampleCursorSyncInfo

The synchronization information for the current sample for consideration when resynchronizing a decoder.

struct AVSampleCursorSyncInfo

A structure that describes the attributes of media samples to consider when resynchronizing a decoder.

func copyCurrentSampleFormatDescription() -> CMFormatDescription

Returns the format description of the sample at the cursor’s current position.

var currentSampleAudioDependencyInfo: AVSampleCursorAudioDependencyInfo

The independent decodability information for the audio sample.

var currentSampleDependencyAttachments: [AnyHashable : Any]?

A dictionary of dependency-related sample buffer attachments.

### Accessing Samples

func maySamplesWithEarlierDecodeTimeStampsHavePresentationTimeStamps(laterThan: AVSampleCursor) -> Bool

Determines whether a sample earlier in decode order can have a presentation timestamp later than that of the specified sample cursor.

func maySamplesWithLaterDecodeTimeStampsHavePresentationTimeStamps(earlierThan: AVSampleCursor) -> Bool

Determines whether a sample later in decode order can have a presentation timestamp earlier than that of the specified sample cursor.

var samplesRequiredForDecoderRefresh: Int

The number of samples prior to the current sample, in decode order, the decoder requires to achieve a coherent output at the current decode time.

### Comparing Sample Cursors

func comparePositionInDecodeOrder(withPositionOf: AVSampleCursor) -> ComparisonResult

Compares the relative positions of two sample cursors and returns their relative positions.

## Relationships

### Inherits From

- NSObject

### Conforms To

- CVarArg
- CustomDebugStringConvertible
- CustomStringConvertible
- Equatable
- Hashable
- NSCopying
- NSObjectProtocol
- Sendable

## See Also

### Sample cursors

struct AVSampleCursorSyncInfo

A structure that describes the attributes of media samples to consider when resynchronizing a decoder.

struct AVSampleCursorDependencyInfo

A value for describing dependencies between a media sample and other media samples in the same sample sequence.

struct AVSampleCursorAudioDependencyInfo

A structure that describes the independent decodability of audio samples.

struct AVSampleCursorStorageRange

A structure that indicates the offset and length of storage for a media sample or its chunk.

struct AVSampleCursorChunkInfo

A value that provides information about a chunk of media samples.

