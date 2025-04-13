

- AVFoundation
- AVCaptionRegion
-  identifier 

Instance Property

# identifier

A string that identifies the region.

iOS 18.0+iPadOS 18.0+Mac Catalyst 15.0+macOS 12.0+

``` source
var identifier: String? { get }
```

## Discussion

The system considers two regions the same if their region identifier is equal. Your app needs to ensure that equal caption regions have the same property values.

If this value is `nil`, the system instead treats two regions equal if their `position` and `endPosition` are the same. Captions referring to these regions belong to the same region when the system serializes them to a format like TTML.

