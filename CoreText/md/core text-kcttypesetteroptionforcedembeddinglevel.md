

- Core Text
-  kCTTypesetterOptionForcedEmbeddingLevel 

Global Variable

# kCTTypesetterOptionForcedEmbeddingLevel

A key that specifies the embedding level of the typesetter’s text.

iOS 3.2+iPadOS 3.2+Mac Catalyst 13.1+macOS 10.5+tvOS 9.0+visionOS 1.0+watchOS 2.0+

``` source
let kCTTypesetterOptionForcedEmbeddingLevel: CFString
```

## Discussion

The value for this key must be a `CFNumberRef` object. There’s no default value.

Normally, typesetting applies the Unicode Bidirectional Algorithm as described in Unicode Standard Annex #9. If present, this option specifies the embedding level, and the text system ignores any directional control characters.

## See Also

### Constants

let kCTTypesetterOptionAllowUnboundedLayout: CFString

A key that specifies whether the text system lays out text that requires unreasonable effort.

let kCTTypesetterOptionDisableBidiProcessing: CFStringDeprecated

