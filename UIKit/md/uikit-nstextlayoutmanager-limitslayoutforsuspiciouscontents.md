

- UIKit
- NSTextLayoutManager
-  limitsLayoutForSuspiciousContents 

Instance Property

# limitsLayoutForSuspiciousContents

A Boolean value that controls internal security analysis for malicious inputs and activates defensive behaviors.

iOS 15.0+iPadOS 15.0+Mac Catalyst 15.0+tvOS 15.0+visionOS 1.0+

``` source
var limitsLayoutForSuspiciousContents: Bool { get set }
```

## Discussion

By enabling this functionality, it’s possible that certain text — such as a very long paragraph — might result in an unexpected layout. Defaults to `false`.

## See Also

### Configuring global layout manager options

var layoutQueue: OperationQueue?

The queue that the framework dispatches layout operations on.

var renderingAttributesValidator: ((NSTextLayoutManager, NSTextLayoutFragment) -> Void)?

A callback block that the framework invokes whenever the text layout manager needs to validate the rendering attributes for the range.

var usesFontLeading: Bool

A Boolean value that controls whether the framework uses the leading information specified by the font when laying out text.

var usesHyphenation: Bool

A Boolean values that controls whether the text layout manager attempts to hyphenate when wrapping lines.

