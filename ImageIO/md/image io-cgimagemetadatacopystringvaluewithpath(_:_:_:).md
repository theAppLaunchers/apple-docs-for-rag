

- Image I/O
-  CGImageMetadataCopyStringValueWithPath(\_:\_:\_:) 

Function

# CGImageMetadataCopyStringValueWithPath(\_:\_:\_:)

Searches the metadata for the specified tag, and returns its string value if it exists.

iOS 7.0+iPadOS 7.0+Mac Catalyst 13.1+macOS 10.8+tvOS 9.0+visionOS 1.0+watchOS 2.0+

``` source
func CGImageMetadataCopyStringValueWithPath(
    _ metadata: CGImageMetadata,
    _ parent: CGImageMetadataTag?,
    _ path: CFString
) -> CFString?
```

## Parameters 

`metadata`  

The metadata object to search.

`parent`  

The parent tag, if any. Specify `NULL` to start the search in the top-level tags of the metadata object. If this parameter is `NULL`, you must include a valid prefix string in the `path` parameter.

`path`  

A string that represents the path to the tag. A path consists of the tag’s name, plus optional prefix and parent information. Separate prefix information from other path information using a colon (`:`) character. Separate parent and child tags using the period (`.`) character. For example, the string `“exif:Flash.RedEyeMode”` represents the path to the `RedEyeMode` field of the `Flash` parent structure in the EXIF metadata.

When a tag contains an ordered or unordered array, specify elements using a `0`-based index inside square brackets. For example, use the string `“dc.subject[2]”` to access the third element in the `subject` array.

When the tag contains an alternate-text array, access elements using an RFC 3066 language code inside square brackets. For example, use the string `“dc.description[de]”` to access the German description information.

Use the ? character to delimit qualifiers for tags with string values. You may not use this character for arrays and structures.

## Return Value

The string value for the specified tag, or `NULL` if the tag wasn’t found or doesn’t contain a string value.

## Discussion

The XMP type of the property at the specified path must be CGImageMetadataType.string or CGImageMetadataType.alternateText. If the property contains alternate text, this function returns the element with the `x-default` language qualifier.

## See Also

### Getting the Metadata Tags

func CGImageMetadataCopyTagWithPath(CGImageMetadata, CGImageMetadataTag?, CFString) -> CGImageMetadataTag?

Searches for a specific metadata tag within a metadata collection.

func CGImageMetadataCopyTags(CGImageMetadata) -> CFArray?

Returns an array of root-level metadata tags from the specified metadata object.

func CGImageMetadataCopyTagMatchingImageProperty(CGImageMetadata, CFString, CFString) -> CGImageMetadataTag?

Searches for the specified image property and, if found, returns the corresponding tag object.

