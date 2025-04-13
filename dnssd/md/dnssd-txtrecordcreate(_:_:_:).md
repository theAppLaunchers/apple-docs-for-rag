

- dnssd
-  TXTRecordCreate(\_:\_:\_:) 

Function

# TXTRecordCreate(\_:\_:\_:)

Creates a new empty TXTRecordRef referencing the specified storage.

iOS 10.0+iPadOS 10.0+Mac Catalyst 13.0+macOS 10.12+tvOS 10.0+visionOS 1.0+watchOS 3.0+

``` source
func TXTRecordCreate(
    _ txtRecord: UnsafeMutablePointer!,
    _ bufferLen: UInt16,
    _ buffer: UnsafeMutableRawPointer!
)
```

## Parameters 

`txtRecord`  

A pointer to an uninitialized TXTRecordRef.

`bufferLen`  

The size of the storage provided in the “buffer” parameter.

`buffer`  

Optional caller-supplied storage used to hold the TXTRecord data. This storage must remain valid for as long as the TXTRecordRef.

## Discussion

If the buffer parameter is NULL, or the specified storage size is not large enough to hold a key subsequently added using TXTRecordSetValue(), then additional memory will be added as needed using malloc().

On some platforms, when memory is low, malloc() may fail. In this case, TXTRecordSetValue() will return kDNSServiceErr_NoMemory, and this error condition will need to be handled as appropriate by the caller.

You can avoid the need to handle this error condition if you ensure that the storage you initially provide is large enough to hold all the key/value pairs that are to be added to the record. The caller can precompute the exact length required for all of the key/value pairs to be added, or simply provide a fixed-sized buffer known in advance to be large enough.

A no-value (key-only) key requires (1 + key length) bytes.

A key with empty value requires (1 + key length + 1) bytes.

A key with non-empty value requires (1 + key length + 1 + value length).

For most applications, DNS-SD TXT records are generally less than 100 bytes, so in most cases a simple fixed-sized 256-byte buffer will be more than sufficient.

Recommended size limits for DNS-SD TXT Records are discussed in dns-sd.org

Note: When passing parameters to and from these TXT record APIs, the key name does not include the ‘=’ character. The ‘=’ character is the separator between the key and value in the on-the-wire packet format; it is not part of either the key or the value.

## See Also

### TXT Record Construction Functions

func TXTRecordDeallocate(UnsafeMutablePointer&lt;TXTRecordRef>!)

Releases resources associated with a TXT record.

func TXTRecordGetBytesPtr(UnsafePointer&lt;TXTRecordRef>!) -> UnsafeRawPointer!

Allows you to retrieve a pointer to the raw bytes within a TXTRecordRef.

func TXTRecordGetLength(UnsafePointer&lt;TXTRecordRef>!) -> UInt16

Allows you to determine the length of the raw bytes within a TXTRecordRef.

func TXTRecordRemoveValue(UnsafeMutablePointer&lt;TXTRecordRef>!, UnsafePointer&lt;CChar>!) -> DNSServiceErrorType

Removes a key from a TXTRecordRef.

func TXTRecordSetValue(UnsafeMutablePointer&lt;TXTRecordRef>!, UnsafePointer&lt;CChar>!, UInt8, UnsafeRawPointer!) -> DNSServiceErrorType

Adds a key (optionally with value) to a TXTRecordRef.

