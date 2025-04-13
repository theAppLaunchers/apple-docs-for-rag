

- Core Media
-  CMAudioSampleBufferCreateWithPacketDescriptionsAndMakeDataReadyHandler(\_:\_:\_:\_:\_:\_:\_:\_:\_:) 

Function

# CMAudioSampleBufferCreateWithPacketDescriptionsAndMakeDataReadyHandler(\_:\_:\_:\_:\_:\_:\_:\_:\_:)

Creates a sample buffer with packet descriptions and a handler to make the data ready for use.

iOS 12.2+iPadOS 12.2+Mac Catalyst 13.1+macOS 10.14.4+tvOS 12.2+visionOS 1.0+watchOS 6.0+

``` source
func CMAudioSampleBufferCreateWithPacketDescriptionsAndMakeDataReadyHandler(
    _ allocator: CFAllocator?,
    _ dataBuffer: CMBlockBuffer?,
    _ dataReady: Bool,
    _ formatDescription: CMFormatDescription,
    _ numSamples: CMItemCount,
    _ presentationTimeStamp: CMTime,
    _ packetDescriptions: UnsafePointer?,
    _ sampleBufferOut: UnsafeMutablePointer,
    _ makeDataReadyHandler: CMSampleBufferMakeDataReadyHandler?
) -> OSStatus
```

## Parameters 

`allocator`  

The allocator to use to create a sample buffer object. Pass kCFAllocatorDefault to use the default allocator.

`dataBuffer`  

A block buffer that contains the media data. This argument can be `NULL`, such as for a block buffer that doesn’t yet have backing memory or data.

`dataReady`  

A Boolean value that indicates whether the buffer already contains the data.

`formatDescription`  

A description of the media data’s format. Must not be `NULL`.

`numSamples`  

The number of samples in the sample buffer. Must not be `0`.

`presentationTimeStamp`  

The timestamp of the first sample in the buffer. Must be a numeric CMTime.

`packetDescriptions`  

An array of packet descriptions, one for each of sample. This value may `NULL` if you know the samples have a constant size and number of frames per packet.

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

func CMSampleBufferCreateWithMakeDataReadyHandler(CFAllocator?, CMBlockBuffer?, Bool, CMFormatDescription?, CMItemCount, CMItemCount, UnsafePointer&lt;CMSampleTimingInfo>?, CMItemCount, UnsafePointer&lt;Int>?, UnsafeMutablePointer&lt;CMSampleBuffer?>, CMSampleBufferMakeDataReadyHandler?) -> OSStatus

Creates a sample buffer with a handler to make the data ready for use.

func CMSampleBufferCreateForImageBufferWithMakeDataReadyHandler(CFAllocator?, CVImageBuffer, Bool, CMVideoFormatDescription, UnsafePointer&lt;CMSampleTimingInfo>, UnsafeMutablePointer&lt;CMSampleBuffer?>, CMSampleBufferMakeDataReadyHandler?) -> OSStatus

Creates a sample buffer with an image buffer and a handler to make the data ready for use.

func CMSampleBufferCreate(allocator: CFAllocator?, dataBuffer: CMBlockBuffer?, dataReady: Bool, makeDataReadyCallback: CMSampleBufferMakeDataReadyCallback?, refcon: UnsafeMutableRawPointer?, formatDescription: CMFormatDescription?, sampleCount: CMItemCount, sampleTimingEntryCount: CMItemCount, sampleTimingArray: UnsafePointer&lt;CMSampleTimingInfo>?, sampleSizeEntryCount: CMItemCount, sampleSizeArray: UnsafePointer&lt;Int>?, sampleBufferOut: UnsafeMutablePointer&lt;CMSampleBuffer?>) -> OSStatus

Creates a sample buffer with a callback to make the data ready for use.

func CMSampleBufferCreateForImageBuffer(allocator: CFAllocator?, imageBuffer: CVImageBuffer, dataReady: Bool, makeDataReadyCallback: CMSampleBufferMakeDataReadyCallback?, refcon: UnsafeMutableRawPointer?, formatDescription: CMVideoFormatDescription, sampleTiming: UnsafePointer&lt;CMSampleTimingInfo>, sampleBufferOut: UnsafeMutablePointer&lt;CMSampleBuffer?>) -> OSStatus

Creates a sample buffer with an image buffer and a callback to make the data ready for use.

func CMAudioSampleBufferCreateWithPacketDescriptions(allocator: CFAllocator?, dataBuffer: CMBlockBuffer?, dataReady: Bool, makeDataReadyCallback: CMSampleBufferMakeDataReadyCallback?, refcon: UnsafeMutableRawPointer?, formatDescription: CMFormatDescription, sampleCount: CMItemCount, presentationTimeStamp: CMTime, packetDescriptions: UnsafePointer&lt;AudioStreamPacketDescription>?, sampleBufferOut: UnsafeMutablePointer&lt;CMSampleBuffer?>) -> OSStatus

Creates a sample buffer with packet descriptions and a callback to make the data ready for use.

