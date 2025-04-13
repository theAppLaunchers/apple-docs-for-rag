

- Core Media
-  CMMetadataCreateIdentifierForKeyAndKeySpace(allocator:key:keySpace:identifierOut:) 

Function

# CMMetadataCreateIdentifierForKeyAndKeySpace(allocator:key:keySpace:identifierOut:)

Creates a URL-like string identifier that represents a key or keyspace tuple.

iOS 8.0+iPadOS 8.0+Mac Catalyst 13.1+macOS 10.10+tvOS 9.0+visionOS 1.0+watchOS 6.0+

``` source
func CMMetadataCreateIdentifierForKeyAndKeySpace(
    allocator: CFAllocator?,
    key: CFTypeRef,
    keySpace: CFString,
    identifierOut: UnsafeMutablePointer
) -> OSStatus
```

## Parameters 

`allocator`  

The allocator to use for creating the identifier.

`key`  

Key data; may be `CFString`, `CFNumber`, or `CFData`.

`keySpace`  

Keyspace; must be string of one to four printable ASCII characters.

`identifierOut`  

Upon return, a pointer to the created identifier.

## Return Value

If successful, a nonzero result code. See Metadata Identifier Error Codes.

## Discussion

Metadata entities are identified by a key whose interpretation is defined by its keyspace. When writing metadata to a QuickTime Movie, this tuple is part of the track’s format description.

See Metadata Identifier Keyspaces for the current list of supported keyspaces and the requirements for key values in each keyspace.

As a matter of convenience, known keyspaces allow for a key to be passed in using a variety of `CFType`s. Note that what is returned by CMMetadataCreateKeyFromIdentifier(allocator:identifier:keyOut:) depends upon the keyspace, and may be a different `CFType` than what is passed to this routine (see the discussion below for what `CFType`s are returned for known keyspaces). To get a key represented as `CFData`, call CMMetadataCreateKeyFromIdentifierAsCFData(allocator:identifier:keyOut:).

Some keyspaces use `OSType`s (a.k.a. `FourCharCode`s) to define their keys, and as such their keys are four bytes in length. For these keyspaces, a key may be passed as a `CFNumber`, a `CFString`, or a `CFData`. A key passed as a `CFNumber` will have its value retrieved as CFNumberType.sInt32Type comprising the four bytes of the key’s numeric value in big-endian byte order. A key passed as a `CFString` must be a valid ASCII string of four characters. A key passed as a `CFData` must be comprised of the four bytes of the key’s numeric value in big-endian byte order.

All other keyspaces allow the key to be passed as a `CFString` or `CFData`. In both cases, the key will be interpreted as an ASCII string for the purposes of identifier encoding.

## See Also

### Creating Metadata Identifiers

func CMMetadataCreateKeyFromIdentifier(allocator: CFAllocator?, identifier: CFString, keyOut: UnsafeMutablePointer&lt;CFTypeRef?>) -> OSStatus

Creates a copy of the key by using an identifier.

func CMMetadataCreateKeyFromIdentifierAsCFData(allocator: CFAllocator?, identifier: CFString, keyOut: UnsafeMutablePointer&lt;CFData?>) -> OSStatus

Creates a copy of the key by using an identifier, and results in a core foundation data object.

func CMMetadataCreateKeySpaceFromIdentifier(allocator: CFAllocator?, identifier: CFString, keySpaceOut: UnsafeMutablePointer&lt;CFString?>) -> OSStatus

Creates a copy of the keyspace by using an identifier.

