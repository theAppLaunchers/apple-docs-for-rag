

- UIKit
- UIPrintPageRenderer
-  numberOfPages 

Instance Property

# numberOfPages

The number of pages to render.

iOS 4.2+iPadOS 4.2+Mac Catalyst 13.1+visionOS 1.0+

``` source
@MainActor
var numberOfPages: Int { get }
```

## Discussion

By default, returns the number of pages as calculated by UIKit if the receiver uses print formatters. If the page renderer uses no print formatters, the returned value is zero. If your page renderer is doing any custom drawing except for headers and footers, it must override this method.

This method is called at any point when UIKit needs the number of pages. If an application requests the page range control, it’s called early on. It can also be called when the selected printer or duplex mode changes. Otherwise, it is called when the print job starts.

If print formatters aren’t used to compute the page count, the page renderer can override this method to calculate and return the number of pages. The computation can take into account the current printableRect value for each page, any implicit margins, and the content to be drawn when laid out within these boundaries.

## See Also

### Related Documentation

var pageCount: Int

The number of pages to print.

### Accessing information about the print job

var paperRect: CGRect

The size of the paper for printing.

var printableRect: CGRect

The area in which printing can occur.

