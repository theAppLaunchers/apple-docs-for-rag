

- UIKit
-  UIMarkupTextPrintFormatter 

Class

# UIMarkupTextPrintFormatter

An object that lays out HTML text for a multipage print job.

iOS 4.2+iPadOS 4.2+Mac Catalyst 13.1+visionOS 1.0+

``` source
@MainActor
class UIMarkupTextPrintFormatter
```

## Overview

To use this print formatter for a print job, create an instance of UIMarkupTextPrintFormatter initialized with the HTML, set the inherited layout properties, and add the object to the print job in one of two ways:

- If a single print formatter is being used for the print job (with no additional drawing), assign it to the printFormatter property of the UIPrintInteractionController shared instance. The inherited startPage property identifies the beginning page of content with which the formatter is associated.

- If you are using multiple formatters along with a page renderer, associate each print formatter with a starting page of the printed content. You often take this approach when you want to add content such as headers and footers to what the formatters provide. You have two ways of associating a print formatter with a UIPrintPageRenderer object:

- You can add print formatters to the printFormatters property of the UIPrintPageRenderer object; the startPage property of the print formatter specifies the starting page.

- You can add print formatters by calling addPrintFormatter(_:startingAtPageAt:) for each print formatter; the second parameter of this method specifies the starting page (and overrides any startPage value).

You can change the markup text at any time before the drawing of the printable content begins.

## Topics

### Creating a markup-text print formatter

init(markupText: String)

Returns a markup-text print formatter initialized with an HTML string.

### Getting and setting the markup text

var markupText: String?

The HTML markup text for the print formatter.

## Relationships

### Inherits From

- UIPrintFormatter

### Conforms To

- CVarArg
- CustomDebugStringConvertible
- CustomStringConvertible
- Equatable
- Hashable
- NSCopying
- NSObjectProtocol

## See Also

### Formatters

class UIPrintFormatter

An abstract base class for print formatters, which are objects that lay out custom printable content that can cross page boundaries.

class UIViewPrintFormatter

An object that lays out the drawn content of a view for printing.

class UISimpleTextPrintFormatter

An object that lays out plain text for printing, possibly over multiple pages.

