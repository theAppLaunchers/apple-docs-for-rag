*   [AVFoundation](/documentation/avfoundation)
*   AVCaption

Class

# AVCaption

An object that represents text to present over a time range.

iOS 18.0+iPadOS 18.0+Mac Catalyst 15.0+macOS 12.0+

```swift
```swift
```swift
```swift
```swift
```swift
```swift
```swift
class AVCaption
```
```
```
```
```
```
```
```

## [Overview](/documentation/AVFoundation/AVCaption#overview)

A caption contains a cue, which is a single sentence or paragraph of text for a time range in the video timeline. Within the active range, the caption may animate (for example, Karaoke lyrics) by rolling-up, changing visibility, or using other dynamic styling.

## [Topics](/documentation/AVFoundation/AVCaption#topics)

### [Creating a Caption](/documentation/AVFoundation/AVCaption#Creating-a-Caption)

[`init(String, timeRange: CMTimeRange)`](/documentation/avfoundation/avcaption/init\(_:timerange:\))

Creates a caption that contains text and a time range.

### [Accessing Text and Timing](/documentation/AVFoundation/AVCaption#Accessing-Text-and-Timing)

```swift
```swift
```swift
```swift
var text: String
```
```

The caption text.
```
```swift
```swift
```swift
var timeRange: CMTimeRange
```
```

The time range over which the system presents the caption.
```
```

### [Accessing the Region](/documentation/AVFoundation/AVCaption#Accessing-the-Region)

```swift
```swift
```swift
```swift
var region: AVCaptionRegion?
```
```

The region in which the caption exists.
```
```

### [Accessing Font Styles](/documentation/AVFoundation/AVCaption#Accessing-Font-Styles)

```swift
```swift
```swift
```swift
func fontStyle(at: String.Index) -> (AVCaption.FontStyle, Range<String.Index>)
```
```

Returns the font style and range at the index position.
```
```swift
```swift
```swift
enum FontStyle
```
```

Font styles for caption text.
```
```swift
```swift
```swift
func fontWeight(at: String.Index) -> (AVCaption.FontWeight, Range<String.Index>)
```
```

Returns the font weight and range at the index position.
```
```swift
```swift
```swift
enum FontWeight
```
```

Font weights for a caption.
```
```swift
```swift
```swift
func decoration(at: String.Index) -> (AVCaption.Decoration, Range<String.Index>)
```
```

Returns the text decoration at the index position.
```
```swift
```swift
```swift
struct Decoration
```
```

Text decorations for caption text.
```
```

### [Accessing Colors](/documentation/AVFoundation/AVCaption#Accessing-Colors)

```swift
```swift
```swift
```swift
func textColor(at: String.Index) -> (CGColor?, Range<String.Index>)
```
```

Returns the text color at the index position.
```
```swift
```swift
```swift
func backgroundColor(at: String.Index) -> (CGColor?, Range<String.Index>)
```
```

Returns the background color at the index position.
```
```

### [Accessing Alignment](/documentation/AVFoundation/AVCaption#Accessing-Alignment)

```swift
```swift
```swift
```swift
var textAlignment: AVCaption.TextAlignment
```
```

The alignment for the caption text.
```
```swift
```swift
```swift
enum TextAlignment
```
```

Text alignment options for a caption.
```
```

### [Accessing Animation](/documentation/AVFoundation/AVCaption#Accessing-Animation)

```swift
```swift
```swift
```swift
var animation: AVCaption.Animation
```
```

The animation that the system applies to this caption.
```
```swift
```swift
```swift
enum Animation
```
```

Animation options for a caption.
```
```

### [Accessing Advanced Typography](/documentation/AVFoundation/AVCaption#Accessing-Advanced-Typography)

```swift
```swift
```swift
```swift
func ruby(at: String.Index) -> (AVCaption.Ruby?, Range<String.Index>)
```
```

Returns the ruby text at the index position.
```
```swift
```swift
```swift
class Ruby
```
```

An object that presents ruby characters.
```
```swift
```swift
```swift
func textCombine(at: String.Index) -> (AVCaption.TextCombine, Range<String.Index>)
```
```

Returns the text combine at the index position.
```
```swift
```swift
```swift
enum TextCombine
```
```

The caption’s supported rendering policy options.
```
```

## [Relationships](/documentation/AVFoundation/AVCaption#relationships)

### [Inherits From](/documentation/AVFoundation/AVCaption#inherits-from)

*   [`NSObject`](/documentation/ObjectiveC/NSObject-swift.class)

### [Inherited By](/documentation/AVFoundation/AVCaption#inherited-by)

*   [`AVMutableCaption`](/documentation/avfoundation/avmutablecaption)

### [Conforms To](/documentation/AVFoundation/AVCaption#conforms-to)

*   [`CVarArg`](/documentation/Swift/CVarArg)
*   [`CustomDebugStringConvertible`](/documentation/Swift/CustomDebugStringConvertible)
*   [`CustomStringConvertible`](/documentation/Swift/CustomStringConvertible)
*   [`Equatable`](/documentation/Swift/Equatable)
*   [`Hashable`](/documentation/Swift/Hashable)
*   [`NSCoding`](/documentation/Foundation/NSCoding)
*   [`NSCopying`](/documentation/Foundation/NSCopying)
*   [`NSMutableCopying`](/documentation/Foundation/NSMutableCopying)
*   [`NSObjectProtocol`](/documentation/ObjectiveC/NSObjectProtocol)
*   [`NSSecureCoding`](/documentation/Foundation/NSSecureCoding)

## [See Also](/documentation/AVFoundation/AVCaption#see-also)

### [Captions](/documentation/AVFoundation/AVCaption#Captions)

```swift
```swift
```swift
```swift
class AVMutableCaption
```
```

A mutable caption subclass that you use to create new captions.
```
```