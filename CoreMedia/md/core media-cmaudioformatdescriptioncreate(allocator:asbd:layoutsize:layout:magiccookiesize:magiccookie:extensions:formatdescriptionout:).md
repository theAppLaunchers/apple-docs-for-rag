

- Core Media
-  CMAudioFormatDescriptionCreate(allocator:asbd:layoutSize:layout:magicCookieSize:magicCookie:extensions:formatDescriptionOut:) 

Function

# CMAudioFormatDescriptionCreate(allocator:asbd:layoutSize:layout:magicCookieSize:magicCookie:extensions:formatDescriptionOut:)

Creates a format description for an audio media stream.

iOS 4.0+iPadOS 4.0+Mac Catalyst 13.1+macOS 10.7+tvOS 9.0+visionOS 1.0+watchOS 6.0+

``` source
func CMAudioFormatDescriptionCreate(
    allocator: CFAllocator?,
    asbd: UnsafePointer,
    layoutSize: Int,
    layout: UnsafePointer?,
    magicCookieSize: Int,
    magicCookie: UnsafeRawPointer?,
    extensions: CFDictionary?,
    formatDescriptionOut: UnsafeMutablePointer
) -> OSStatus
```

## Parameters 

`allocator`  

`CFAllocator` to be used. Pass `kCFAllocatorDefault` or `NULL` to use the default allocator.

`asbd`  

Audio format description (see `CoreAudioTypes.h`). This information is required.

`layoutSize`  

Size, in bytes, of audio channel layout. 0 if layout is `NULL`.

`layout`  

Audio channel layout (see CoreAudioTypes.h). Can be `NULL`.

`magicCookieSize`  

Size, in bytes, of magic cookie. 0 if `magicCookie` is `NULL`.

`magicCookie`  

Magic cookie. This information is required for some formats, and must be `NULL` for all others.

`extensions`  

Dictionary of extension key/value pairs. Keys are always `CFStrings`. Values are always property list objects (ie. `CFData`, `CFString`, `CFArray`, `CFDictionary`, `CFDate`, `CFBoolean`, or `CFNumber`). Can be `NULL`.

`formatDescriptionOut`  

On output, returns the newly created audio `CMFormatDescription`.

## Return Value

A result code.

## Discussion

The `absd` is required, the channel layout is optional, and the magic cookie is required for some compression formats (and must be NULL for all others). The caller owns the returned `CMFormatDescription`, and must release it when done with it. The `ASBD`, magic cookie, channel layout, and extensions are all copied (the extensions are deep-copied). The caller can deallocate them or re-use them after making this call.

## See Also

### Working with Audio Descriptions

struct CMSoundDescriptionFlavor

Types that represent sound format descriptions.

func CMAudioFormatDescriptionCreateSummary(allocator: CFAllocator?, formatDescriptionArray: CFArray, flags: UInt32, formatDescriptionOut: UnsafeMutablePointer&lt;CMAudioFormatDescription?>) -> OSStatus

Creates a summary audio format description from an array of descriptions.

func CMAudioFormatDescriptionEqual(CMAudioFormatDescription, otherFormatDescription: CMAudioFormatDescription, equalityMask: CMAudioFormatDescriptionMask, equalityMaskOut: UnsafeMutablePointer&lt;CMAudioFormatDescriptionMask>?) -> Bool

Returns a Boolean value that indicates whether the two audio format descriptions are equal.

func CMAudioFormatDescriptionGetChannelLayout(CMAudioFormatDescription, sizeOut: UnsafeMutablePointer&lt;Int>?) -> UnsafePointer&lt;AudioChannelLayout>?

Returns a read-only pointer to, and the size of, the audio channel layout inside an audio format description.

func CMAudioFormatDescriptionGetFormatList(CMAudioFormatDescription, sizeOut: UnsafeMutablePointer&lt;Int>?) -> UnsafePointer&lt;AudioFormatListItem>?

Returns a read-only pointer to, and size of, the array of audio format list item structures in an audio format description.

func CMAudioFormatDescriptionGetMagicCookie(CMAudioFormatDescription, sizeOut: UnsafeMutablePointer&lt;Int>?) -> UnsafeRawPointer?

Returns a read-only pointer to, and size of, the magic cookie in an audio format description.

func CMAudioFormatDescriptionGetMostCompatibleFormat(CMAudioFormatDescription) -> UnsafePointer&lt;AudioFormatListItem>?

Returns a read-only pointer to the appropriate audio format list item in an audio format description.

func CMAudioFormatDescriptionGetRichestDecodableFormat(CMAudioFormatDescription) -> UnsafePointer&lt;AudioFormatListItem>?

Returns a read-only pointer to the appropriate audio format list item in an audio format description.

func CMAudioFormatDescriptionGetStreamBasicDescription(CMAudioFormatDescription) -> UnsafePointer&lt;AudioStreamBasicDescription>?

Returns a read-only pointer to the audio stream description in an audio format description.

func CMDoesBigEndianSoundDescriptionRequireLegacyCBRSampleTableLayout(CMBlockBuffer, flavor: CMSoundDescriptionFlavor?) -> Bool

Returns a Boolean value that indicates whether the sample tables need to use the legacy constant bit-rate encoding layout.

func CMSwapBigEndianSoundDescriptionToHost(UnsafeMutablePointer&lt;UInt8>, Int) -> OSStatus

Converts a sound description data structure from big-endian to host-endian, in place.

func CMSwapHostEndianSoundDescriptionToBig(UnsafeMutablePointer&lt;UInt8>, Int) -> OSStatus

Converts a sound description data structure from host-endian to big-endian, in place.

func CMAudioFormatDescriptionCreateFromBigEndianSoundDescriptionData(allocator: CFAllocator?, bigEndianSoundDescriptionData: UnsafePointer&lt;UInt8>, size: Int, flavor: CMSoundDescriptionFlavor?, formatDescriptionOut: UnsafeMutablePointer&lt;CMAudioFormatDescription?>) -> OSStatus

Creates an audio format description from a big-endian sound description data structure.

func CMAudioFormatDescriptionCreateFromBigEndianSoundDescriptionBlockBuffer(allocator: CFAllocator?, bigEndianSoundDescriptionBlockBuffer: CMBlockBuffer, flavor: CMSoundDescriptionFlavor?, formatDescriptionOut: UnsafeMutablePointer&lt;CMAudioFormatDescription?>) -> OSStatus

Creates an audio format description from a big-endian sound description data structure in a buffer.

func CMAudioFormatDescriptionCopyAsBigEndianSoundDescriptionBlockBuffer(allocator: CFAllocator?, audioFormatDescription: CMAudioFormatDescription, flavor: CMSoundDescriptionFlavor?, blockBufferOut: UnsafeMutablePointer&lt;CMBlockBuffer?>) -> OSStatus

Copies the contents of an audio format description to a buffer in big-endian byte ordering.

