

- Core Media
-  CMSampleBufferCreateWithMakeDataReadyHandler(\_:\_:\_:\_:\_:\_:\_:\_:\_:\_:\_:) 

Function

# CMSampleBufferCreateWithMakeDataReadyHandler(\_:\_:\_:\_:\_:\_:\_:\_:\_:\_:\_:)

Creates a sample buffer with a handler to make the data ready for use.

iOS 12.2+iPadOS 12.2+Mac Catalyst 13.1+macOS 10.14.4+tvOS 12.2+visionOS 1.0+watchOS 6.0+

``` source
func CMSampleBufferCreateWithMakeDataReadyHandler(
    _ allocator: CFAllocator?,
    _ dataBuffer: CMBlockBuffer?,
    _ dataReady: Bool,
    _ formatDescription: CMFormatDescription?,
    _ numSamples: CMItemCount,
    _ numSampleTimingEntries: CMItemCount,
    _ sampleTimingArray: UnsafePointer?,
    _ numSampleSizeEntries: CMItemCount,
    _ sampleSizeArray: UnsafePointer?,
    _ sampleBufferOut: UnsafeMutablePointer,
    _ makeDataReadyHandler: CMSampleBufferMakeDataReadyHandler?
) -> OSStatus
```

## Parameters 

`allocator`  

The allocator to use to create a sample buffer object. Pass kCFAllocatorDefault to use the default allocator.

`dataBuffer`  

A block buffer that contains the media data. This argument can be `NULL`, such as for a block buffer that doesn’t yet have backing memory or data.

If the buffer contains media data, specify `true` for the `dataReady` argument. Also set `dataReady` to true if the buffer is `NULL` and `numSamples` is `0`.

`dataReady`  

A Boolean value that indicates whether the buffer already contains the data.

`formatDescription`  

A description of the media data’s format, or `NULL` for none.

`numSamples`  

The number of samples in the sample buffer, or `0` if media samples aren’t yet loaded.

`numSampleTimingEntries`  

The number of entries in `sampleTimingArray`. The value must be `0`, `1`, or `numSamples`.

`sampleTimingArray`  

An array of CMSampleTimingInfo structures, one per sample. This value can be `NULL`.

If all samples are in presentation order and have the same duration, pass a timing info structure that you configure as follows:

- Set its duration to the duration of one sample

- Set its presentation timestamp to the presentation time of the numerically earliest sample

- Set the decode timestamp set to invalid.

The system’s behavior isn’t defined if multiple samples in a sample buffer (or even in multiple buffers in the same stream) have the same presentation timestamp.

`numSampleSizeEntries`  

The number of entries in `sampleSizeArray`. The value must be `0`, `1`, or `numSamples`.

`sampleSizeArray`  

An array of size entries, one per sample. If all samples have the same size, you can pass a single size entry containing the size of one sample.

This value can be `NULL`, and must be if the samples aren’t contiguous in the buffer, such as when working with noninterleaved audio.

`sampleBufferOut`  

On return, a new CMSampleBuffer object.

`makeDataReadyHandler`  

A block for the system to call to make the data ready for use. This argument can be `NULL`.

## Topics

### Handlers

typealias CMSampleBufferMakeDataReadyHandler

A block the system calls to make the sample buffer ready for use.

## See Also

### Creating Sample Buffers

func CMSampleBufferCreateReady(allocator: CFAllocator?, dataBuffer: CMBlockBuffer?, formatDescription: CMFormatDescription?, sampleCount: CMItemCount, sampleTimingEntryCount: CMItemCount, sampleTimingArray: UnsafePointer&lt;CMSampleTimingInfo>?, sampleSizeEntryCount: CMItemCount, sampleSizeArray: UnsafePointer&lt;Int>?, sampleBufferOut: UnsafeMutablePointer&lt;CMSampleBuffer?>) -> OSStatus

Creates a sample buffer with media data.

func CMSampleBufferCreateReadyWithImageBuffer(allocator: CFAllocator?, imageBuffer: CVImageBuffer, formatDescription: CMVideoFormatDescription, sampleTiming: UnsafePointer&lt;CMSampleTimingInfo>, sampleBufferOut: UnsafeMutablePointer&lt;CMSampleBuffer?>) -> OSStatus

Creates a sample buffer with image data.

func CMAudioSampleBufferCreateReadyWithPacketDescriptions(allocator: CFAllocator?, dataBuffer: CMBlockBuffer, formatDescription: CMFormatDescription, sampleCount: CMItemCount, presentationTimeStamp: CMTime, packetDescriptions: UnsafePointer&lt;AudioStreamPacketDescription>?, sampleBufferOut: UnsafeMutablePointer&lt;CMSampleBuffer?>) -> OSStatus

Creates a sample buffer with packet descriptions.

func CMSampleBufferCreateForImageBufferWithMakeDataReadyHandler(CFAllocator?, CVImageBuffer, Bool, CMVideoFormatDescription, UnsafePointer&lt;CMSampleTimingInfo>, UnsafeMutablePointer&lt;CMSampleBuffer?>, CMSampleBufferMakeDataReadyHandler?) -> OSStatus

Creates a sample buffer with an image buffer and a handler to make the data ready for use.

func CMAudioSampleBufferCreateWithPacketDescriptionsAndMakeDataReadyHandler(CFAllocator?, CMBlockBuffer?, Bool, CMFormatDescription, CMItemCount, CMTime, UnsafePointer&lt;AudioStreamPacketDescription>?, UnsafeMutablePointer&lt;CMSampleBuffer?>, CMSampleBufferMakeDataReadyHandler?) -> OSStatus

Creates a sample buffer with packet descriptions and a handler to make the data ready for use.

func CMSampleBufferCreate(allocator: CFAllocator?, dataBuffer: CMBlockBuffer?, dataReady: Bool, makeDataReadyCallback: CMSampleBufferMakeDataReadyCallback?, refcon: UnsafeMutableRawPointer?, formatDescription: CMFormatDescription?, sampleCount: CMItemCount, sampleTimingEntryCount: CMItemCount, sampleTimingArray: UnsafePointer&lt;CMSampleTimingInfo>?, sampleSizeEntryCount: CMItemCount, sampleSizeArray: UnsafePointer&lt;Int>?, sampleBufferOut: UnsafeMutablePointer&lt;CMSampleBuffer?>) -> OSStatus

Creates a sample buffer with a callback to make the data ready for use.

func CMSampleBufferCreateForImageBuffer(allocator: CFAllocator?, imageBuffer: CVImageBuffer, dataReady: Bool, makeDataReadyCallback: CMSampleBufferMakeDataReadyCallback?, refcon: UnsafeMutableRawPointer?, formatDescription: CMVideoFormatDescription, sampleTiming: UnsafePointer&lt;CMSampleTimingInfo>, sampleBufferOut: UnsafeMutablePointer&lt;CMSampleBuffer?>) -> OSStatus

Creates a sample buffer with an image buffer and a callback to make the data ready for use.

func CMAudioSampleBufferCreateWithPacketDescriptions(allocator: CFAllocator?, dataBuffer: CMBlockBuffer?, dataReady: Bool, makeDataReadyCallback: CMSampleBufferMakeDataReadyCallback?, refcon: UnsafeMutableRawPointer?, formatDescription: CMFormatDescription, sampleCount: CMItemCount, presentationTimeStamp: CMTime, packetDescriptions: UnsafePointer&lt;AudioStreamPacketDescription>?, sampleBufferOut: UnsafeMutablePointer&lt;CMSampleBuffer?>) -> OSStatus

Creates a sample buffer with packet descriptions and a callback to make the data ready for use.

