

- Core Media
-  CMTimeCodeFormatDescriptionCopyAsBigEndianTimeCodeDescriptionBlockBuffer(allocator:timeCodeFormatDescription:flavor:blockBufferOut:) 

Function

# CMTimeCodeFormatDescriptionCopyAsBigEndianTimeCodeDescriptionBlockBuffer(allocator:timeCodeFormatDescription:flavor:blockBufferOut:)

Copies the contents of a time code format description to a buffer in big-endian byte order.

iOS 8.0+iPadOS 8.0+Mac Catalyst 13.1+macOS 10.10+tvOS 9.0+visionOS 1.0+watchOS 6.0+

``` source
func CMTimeCodeFormatDescriptionCopyAsBigEndianTimeCodeDescriptionBlockBuffer(
    allocator: CFAllocator?,
    timeCodeFormatDescription: CMTimeCodeFormatDescription,
    flavor: CMTimeCodeDescriptionFlavor?,
    blockBufferOut: UnsafeMutablePointer
) -> OSStatus
```

## Parameters 

`allocator`  

Allocator to use for allocating the CMBlockBuffer object. May be NULL.

`timeCodeFormatDescription`  

CMTimeCodeFormatDescription to be copied.

`flavor`  

Reserved for future use. Pass NULL for QuickTime Movie or ISO flavor.

`blockBufferOut`  

Receives new CMBlockBuffer containing TimeCodeDescription data structure in big-endian byte ordering.

## Discussion

On return, the caller owns the returned CMBlockBuffer, and must release it when done with it.

Note

The dataRefIndex field of the SampleDescription is intentionally filled with garbage values (0xFFFF). The caller must overwrite these values with a valid dataRefIndex if writing the SampleDescription to a QuickTime/ISO file.

## See Also

### Working with Time Code Descriptions

struct CMTimeCodeDescriptionFlavor

Types that represent time code format descriptions.

func CMTimeCodeFormatDescriptionCreate(allocator: CFAllocator?, timeCodeFormatType: CMTimeCodeFormatType, frameDuration: CMTime, frameQuanta: UInt32, flags: UInt32, extensions: CFDictionary?, formatDescriptionOut: UnsafeMutablePointer&lt;CMTimeCodeFormatDescription?>) -> OSStatus

Creates a format description for time code media.

func CMTimeCodeFormatDescriptionGetFrameDuration(CMTimeCodeFormatDescription) -> CMTime

Returns the duration of each frame.

func CMTimeCodeFormatDescriptionGetFrameQuanta(CMTimeCodeFormatDescription) -> UInt32

Returns the frames per second for a time code, or frames per tick in counter mode.

func CMTimeCodeFormatDescriptionGetTimeCodeFlags(CMTimeCodeFormatDescription) -> UInt32

Returns time code flags.

func CMTimeCodeFormatDescriptionCreateFromBigEndianTimeCodeDescriptionBlockBuffer(allocator: CFAllocator?, bigEndianTimeCodeDescriptionBlockBuffer: CMBlockBuffer, flavor: CMTimeCodeDescriptionFlavor?, formatDescriptionOut: UnsafeMutablePointer&lt;CMTimeCodeFormatDescription?>) -> OSStatus

Creates a time code format description from a big-endian time code description data structure in a buffer.

func CMTimeCodeFormatDescriptionCreateFromBigEndianTimeCodeDescriptionData(allocator: CFAllocator?, bigEndianTimeCodeDescriptionData: UnsafePointer&lt;UInt8>, size: Int, flavor: CMTimeCodeDescriptionFlavor?, formatDescriptionOut: UnsafeMutablePointer&lt;CMTimeCodeFormatDescription?>) -> OSStatus

Creates a time code format description from a big-endian time code description structure.

func CMSwapBigEndianTimeCodeDescriptionToHost(UnsafeMutablePointer&lt;UInt8>, Int) -> OSStatus

Converts a time code description data structure from big-endian to host-endian, in place.

func CMSwapHostEndianTimeCodeDescriptionToBig(UnsafeMutablePointer&lt;UInt8>, Int) -> OSStatus

Converts a time code description data structure from host-endian to big-endian, in place.

