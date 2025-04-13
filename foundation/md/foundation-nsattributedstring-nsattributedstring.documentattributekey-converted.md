

- Foundation
- NSAttributedString
- NSAttributedString.DocumentAttributeKey
-  converted 

Type Property

# converted

A value that indicates whether a filter service converted the file.

FoundationAppKitmacOS 10.0+

``` source
static let converted: NSAttributedString.DocumentAttributeKey
```

## Discussion

The value of this attribute is an NSNumber object containing an integer. Indicates whether the file was converted by a filter service.

If missing or 0, the file was originally in the format specified by documentType. If negative, the file was originally in the format specified by document type, but the conversion to NSAttributedString may have been lossy. If 1 or more, it was converted to this type by a filter service.

The string constant in macOS 10.3 and earlier is `@"Converted"`.

## See Also

### Getting document metadata keys

static let author: NSAttributedString.DocumentAttributeKey

The author of the document.

static let category: NSAttributedString.DocumentAttributeKey

The document’s category.

static let characterEncoding: NSAttributedString.DocumentAttributeKey

The string encoding for the document.

static let comment: NSAttributedString.DocumentAttributeKey

The document comments.

static let company: NSAttributedString.DocumentAttributeKey

The company or organization name associated with the document.

static let copyright: NSAttributedString.DocumentAttributeKey

The document’s copyright information.

static let creationTime: NSAttributedString.DocumentAttributeKey

The creation date of the document.

static let editor: NSAttributedString.DocumentAttributeKey

The name of person who last edited the document.

static let keywords: NSAttributedString.DocumentAttributeKey

The document keywords.

static let manager: NSAttributedString.DocumentAttributeKey

The name of the author’s manager.

static let modificationTime: NSAttributedString.DocumentAttributeKey

The modification date of the document.

static let readOnly: NSAttributedString.DocumentAttributeKey

An indication of whether the document is read-only.

static let subject: NSAttributedString.DocumentAttributeKey

The subject of the document.

static let title: NSAttributedString.DocumentAttributeKey

The document title.

