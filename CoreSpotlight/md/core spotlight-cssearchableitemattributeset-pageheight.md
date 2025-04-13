

- Core Spotlight
- CSSearchableItemAttributeSet
-  pageHeight 

Instance Property

# pageHeight

The height of the document page, in points (72 points per inch).

iOS 9.0+iPadOS 9.0+Mac Catalyst 13.1+macOS 10.11+visionOS 1.0+

``` source
var pageHeight: NSNumber? { get set }
```

## Discussion

For a PDF document, this property specifies the height of the first page only; other pages in a PDF document may have different heights.

## See Also

### Describing documents

var audiences: [String]?

A class of entity for which the item is intended or useful.

var contentDescription: String?

A description of the item’s content.

var creator: String?

The name of the app that created the content.

var encodingApplications: [String]?

The name of the apps that converted the original content into a PDF stream.

var fileSize: NSNumber?

The size of the document file.

var fontNames: [String]?

An array of font names the document uses.

var identifier: String?

A formal identifier that references the document the item represents.

var kind: String?

A description of the kind of document the item represents.

var pageCount: NSNumber?

The number of pages in the document.

var pageWidth: NSNumber?

The width of the document page, in points (72 points per inch).

var securityMethod: String?

The security method (a type of encryption) that protects the document file.

var subject: String?

The subject of the document.

var theme: String?

The theme of the document.

