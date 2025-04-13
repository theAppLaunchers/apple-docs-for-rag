

- PDFKit
- PDFPage
-  rotation 

Instance Property

# rotation

Sets the rotation angle for the page in degrees.

iOS 11.0+iPadOS 11.0+Mac Catalyst 13.1+macOS 10.4+tvOS 11.0+visionOS 1.0+

``` source
var rotation: Int { get set }
```

## Discussion

The rotation must be a positive or negative multiple of 90 (negative angles are converted to their positive equivalents; for example, -90 is changed to 270); otherwise this method throws an exception.

## See Also

### Getting Information About a Page

var document: PDFDocument?

Returns the `PDFDocument` object with which the page is associated.

var label: String?

Returns the label for the page.

func bounds(for: PDFDisplayBox) -> CGRect

Returns the bounds for the specified PDF display box.

func setBounds(CGRect, for: PDFDisplayBox)

Sets the bounds for the specified box.

