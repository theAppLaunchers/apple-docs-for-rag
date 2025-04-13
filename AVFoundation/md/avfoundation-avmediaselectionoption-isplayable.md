

- AVFoundation
- AVMediaSelectionOption
-  isPlayable 

Instance Property

# isPlayable

A Boolean value that indicates whether the media selection option is playable.

iOS 5.0+iPadOS 5.0+Mac Catalyst 13.1+macOS 10.8+tvOS 9.0+visionOS 1.0+watchOS 1.0+

``` source
var isPlayable: Bool { get }
```

## Discussion

If the media data associated with the option cannot be decoded or otherwise rendered, the value of this property is false.

