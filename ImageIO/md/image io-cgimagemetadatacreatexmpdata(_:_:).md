

- Image I/O
-  CGImageMetadataCreateXMPData(\_:\_:) 

Function

# CGImageMetadataCreateXMPData(\_:\_:)

Returns a data object that contains the metadata object’s contents serialized into the XMP format.

iOS 7.0+iPadOS 7.0+Mac Catalyst 13.1+macOS 10.8+tvOS 9.0+visionOS 1.0+watchOS 2.0+

``` source
func CGImageMetadataCreateXMPData(
    _ metadata: CGImageMetadata,
    _ options: CFDictionary?
) -> CFData?
```

## Parameters 

`metadata`  

The metadata object to serialize. The function converts all tags in this object to XMP data.

`options`  

Additional options for the serialization process. Options aren’t currently supported, so specify `NULL`.

## Return Value

A CFData object with an XMP representation of the metadata, or `NULL` if an error occurs.

## Discussion

Use this function to create sidecar files with metadata for image formats that don’t support embedded XMP, or that you cannot edit due to other format restrictions. For example, use this function to create the data for proprietary RAW camera formats.

