

- PDFKit
- PDFOutline
-  isOpen 

Instance Property

# isOpen

Returns a Boolean value that indicates whether the outline object is initially disclosed.

iOS 11.0+iPadOS 11.0+Mac Catalyst 13.1+macOS 10.5+tvOS 11.0+visionOS 1.0+

``` source
var isOpen: Bool { get set }
```

## Discussion

Calling `isOpen` on an outline object that has no children always returns false. Calling `isOpen` on the root outline object always returns true.

