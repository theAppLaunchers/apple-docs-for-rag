

- AppKit
- NSPrintInfo
-  paperSize 

Instance Property

# paperSize

The size of the paper.

macOS

``` source
var paperSize: NSSize { get set }
```

## Discussion

The size is measured in points in the user coordinate space.

## See Also

### Related Documentation

func dictionary() -> NSMutableDictionary

Returns the print info’s dictionary that contains the printing attributes.

init(dictionary: [NSPrintInfo.AttributeKey : Any])

Returns a printing information object initialized with the parameters in the specified dictionary.

### Managing the Printing Rectangle

var topMargin: CGFloat

The top margin to the specified size.

var bottomMargin: CGFloat

The height of the bottom margin.

var leftMargin: CGFloat

The width of the left margin.

var rightMargin: CGFloat

The width of the right margin.

var imageablePageBounds: NSRect

The imageable area of a sheet of paper specified by the print info.

var orientation: NSPrintInfo.PaperOrientation

The orientation attribute.

enum PaperOrientation

Constants that describe the orientation of printing on a page.

var paperName: NSPrinter.PaperName?

The name of the currently selected paper size.

struct PaperName

The type you use to specify the name of a type of paper.

var localizedPaperName: String?

The human-readable name of the currently selected paper size, suitable for presentation in user interfaces.

