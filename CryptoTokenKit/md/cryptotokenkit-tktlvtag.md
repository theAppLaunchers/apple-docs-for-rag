

- CryptoTokenKit
-  TKTLVTag 

Type Alias

# TKTLVTag

The type used to identify TLV format tags.

iOS 10.0+iPadOS 10.0+Mac Catalyst 13.1+macOS 10.12+tvOS 11.0+visionOS 1.0+watchOS 4.0+

``` source
typealias TKTLVTag = UInt64
```

## Discussion

Although some encodings tags do not have any size restrictions, the CryptoTokenKit framework supports tag lengths only up to 64-bits.

## See Also

### Creating TLV Records

init(tag: TKTLVTag, value: Data)

Initializes a BER-TLV record with the specified tag and value.

init(tag: TKTLVTag, records: [TKTLVRecord])

Initializes a BER-TLV record with the specified tag and an array of TLV subrecords.

