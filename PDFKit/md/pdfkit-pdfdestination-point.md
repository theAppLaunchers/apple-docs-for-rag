

- PDFKit
- PDFDestination
-  point 

Instance Property

# point

Returns the point, in page space, that the destination refers to.

iOS 11.0+iPadOS 11.0+Mac Catalyst 13.1+macOS 10.4+tvOS 11.0+visionOS 1.0+

**macOS**

``` source
var point: NSPoint { get }
```

**iOS, iPadOS, Mac Catalyst, tvOS, visionOS**

``` source
var point: CGPoint { get }
```

## Return Value

The point, in page space, referred to by the destination.

## Discussion

Page space is a 72 dpi coordinate system with the origin at the lower-left corner of the current page.

## See Also

### Getting Pages and Points

var page: PDFPage?

Returns the page that the destination refers to.

let kPDFDestinationUnspecifiedValue: CGFloat

