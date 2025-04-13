

- AVFoundation
- AVMetadataGroup
-  classifyingLabel 

Instance Property

# classifyingLabel

The classifying label associated with the metadata group.

iOS 9.3+iPadOS 9.3+Mac Catalyst 13.1+macOS 10.11.3+tvOS 9.2+visionOS 1.0+watchOS 2.3+

``` source
var classifyingLabel: String? { get }
```

## Discussion

The value of this property may be `nil` if no classifying label is defined for this group.

## See Also

### Inspecting the Metadata Group

var items: [AVMetadataItem]

The array of metadata items associated with the metadata group.

var uniqueID: String?

The unique identifier for the metadata group.

