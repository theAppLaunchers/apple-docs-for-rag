

- Core Media
-  CMTimeCodeFormatDescriptionCreate(allocator:timeCodeFormatType:frameDuration:frameQuanta:flags:extensions:formatDescriptionOut:) 

Function

# CMTimeCodeFormatDescriptionCreate(allocator:timeCodeFormatType:frameDuration:frameQuanta:flags:extensions:formatDescriptionOut:)

Creates a format description for time code media.

iOS 4.0+iPadOS 4.0+Mac Catalyst 13.1+macOS 10.7+tvOS 9.0+visionOS 1.0+watchOS 6.0+

``` source
func CMTimeCodeFormatDescriptionCreate(
    allocator: CFAllocator?,
    timeCodeFormatType: CMTimeCodeFormatType,
    frameDuration: CMTime,
    frameQuanta: UInt32,
    flags: UInt32,
    extensions: CFDictionary?,
    formatDescriptionOut: UnsafeMutablePointer
) -> OSStatus
```

## Parameters 

`allocator`  

Allocator to be used for creating the `CMFormatDescription` object.

`timeCodeFormatType`  

One of the CMTimeCodeFormatType.

`frameDuration`  

Duration of each frame (e.g. `100/2997`).

`frameQuanta`  

Frames/sec for timecode (e.g. 30) OR frames/tick for counter mode.

`flags`  

`kCMTimeCodeFlag_DropFrame`, `kCMTimeCodeFlag_24HourMax`, `kCMTimeCodeFlag_NegTimesOK`. For possible values, see Video Profile Constants.

`extensions`  

Keys are always `CFStrings`. Values are always property list objects (i.e. `CFData`). May be NULL.

`formatDescriptionOut`  

Receives the newly-created `CMFormatDescription`.

## Return Value

A result code. Returns `noErr` if successful.

## Discussion

The caller owns the returned `CMFormatDescription`, and must release it when done with it. All input parameters are copied (the extensions are deep-copied). The caller can deallocate them or re-use them after making this call.

## See Also

### Working with Time Code Descriptions

struct CMTimeCodeDescriptionFlavor

Types that represent time code format descriptions.

func CMTimeCodeFormatDescriptionGetFrameDuration(CMTimeCodeFormatDescription) -> CMTime

Returns the duration of each frame.

func CMTimeCodeFormatDescriptionGetFrameQuanta(CMTimeCodeFormatDescription) -> UInt32

Returns the frames per second for a time code, or frames per tick in counter mode.

func CMTimeCodeFormatDescriptionGetTimeCodeFlags(CMTimeCodeFormatDescription) -> UInt32

Returns time code flags.

func CMTimeCodeFormatDescriptionCopyAsBigEndianTimeCodeDescriptionBlockBuffer(allocator: CFAllocator?, timeCodeFormatDescription: CMTimeCodeFormatDescription, flavor: CMTimeCodeDescriptionFlavor?, blockBufferOut: UnsafeMutablePointer&lt;CMBlockBuffer?>) -> OSStatus

Copies the contents of a time code format description to a buffer in big-endian byte order.

func CMTimeCodeFormatDescriptionCreateFromBigEndianTimeCodeDescriptionBlockBuffer(allocator: CFAllocator?, bigEndianTimeCodeDescriptionBlockBuffer: CMBlockBuffer, flavor: CMTimeCodeDescriptionFlavor?, formatDescriptionOut: UnsafeMutablePointer&lt;CMTimeCodeFormatDescription?>) -> OSStatus

Creates a time code format description from a big-endian time code description data structure in a buffer.

func CMTimeCodeFormatDescriptionCreateFromBigEndianTimeCodeDescriptionData(allocator: CFAllocator?, bigEndianTimeCodeDescriptionData: UnsafePointer&lt;UInt8>, size: Int, flavor: CMTimeCodeDescriptionFlavor?, formatDescriptionOut: UnsafeMutablePointer&lt;CMTimeCodeFormatDescription?>) -> OSStatus

Creates a time code format description from a big-endian time code description structure.

func CMSwapBigEndianTimeCodeDescriptionToHost(UnsafeMutablePointer&lt;UInt8>, Int) -> OSStatus

Converts a time code description data structure from big-endian to host-endian, in place.

func CMSwapHostEndianTimeCodeDescriptionToBig(UnsafeMutablePointer&lt;UInt8>, Int) -> OSStatus

Converts a time code description data structure from host-endian to big-endian, in place.

