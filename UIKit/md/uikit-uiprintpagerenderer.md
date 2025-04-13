

- UIKit
-  UIPrintPageRenderer 

Class

# UIPrintPageRenderer

An object that draws pages of content to print, with or without the assistance of print formatters.

iOS 4.2+iPadOS 4.2+Mac Catalyst 13.1+visionOS 1.0+

``` source
@MainActor
class UIPrintPageRenderer
```

## Overview

A page renderer is an instance of a custom subclass of UIPrintPageRenderer. When you compose a print job using the shared instance of UIPrintInteractionController, you assign the page renderer to the printPageRenderer property of that instance. The subclass typically overrides one or more of the five `draw...` methods.

The drawPage(at:in:) by default calls each of the other draw methods, in the order listed below. Your app can override it if you want to have complete control over what to draw for printing.

- Override drawHeaderForPage(at:in:) to draw content in the header.

- Override drawContentForPage(at:in:) to draw the main content of the print job in the area between the header and the footer.

- Override drawPrintFormatter(_:forPageAt:) to intermix custom drawing with the drawing that an associated print formatter performs. The system calls this method for each print formatter associated with a particular page.

- Override drawFooterForPage(at:in:) to draw content in the footer.

UIPrintPageRenderer usually requires you to specify the number of pages of printable content by overriding numberOfPages. It also allows you to specify the heights of page headers and footers.

You may assign one or more print formatters — UIPrintFormatter objects that can lay out printable content of a certain kind — to specific page ranges of the content. For example, if your printable content is partially HTML, you may assign an instance of the UIMarkupTextPrintFormatter object to the starting page of HTML content. You assign a print formatter using the addPrintFormatter(_:startingAtPageAt:) method and you can get the print formatters for a particular page by calling printFormattersForPage(at:).

## Topics

### Accessing information about the print job

var numberOfPages: Int

The number of pages to render.

var paperRect: CGRect

The size of the paper for printing.

var printableRect: CGRect

The area in which printing can occur.

### Specifying header and footer heights

var headerHeight: CGFloat

The height of the page header.

var footerHeight: CGFloat

The height of the page footer.

### Managing print formatters

func addPrintFormatter(UIPrintFormatter, startingAtPageAt: Int)

Adds a print formatter to the page renderer starting at the specified page.

func printFormattersForPage(at: Int) -> [UIPrintFormatter]?

Returns the print formatters for a specified page.

var printFormatters: [UIPrintFormatter]?

The print formatters for the page renderer.

### Preparing for drawing

func prepare(forDrawingPages: NSRange)

Prepares the renderer for drawing a range of pages.

### Drawing a page

func drawPage(at: Int, in: CGRect)

Draws a page of content for the printer.

func drawHeaderForPage(at: Int, in: CGRect)

Draws the header of a page.

func drawContentForPage(at: Int, in: CGRect)

Draws the content of a page.

func drawPrintFormatter(UIPrintFormatter, forPageAt: Int)

Performs custom drawing in addition to the specified print formatter’s drawing for a page.

func drawFooterForPage(at: Int, in: CGRect)

Draws the footer of a page.

### Managing the rendering quality

func currentRenderingQuality(forRequested: UIPrintRenderingQuality) -> UIPrintRenderingQuality

Determines the actual print-rendering quality according to the requested rendering quality.

enum UIPrintRenderingQuality

Constants that represent the rendering quality for a print operation.

## Relationships

### Inherits From

- NSObject

### Conforms To

- CVarArg
- CustomDebugStringConvertible
- CustomStringConvertible
- Equatable
- Hashable
- NSObjectProtocol
- Sendable

## See Also

### Renderer

Building and improving your app with Mac Catalyst

Improve your iPadOS app with Mac Catalyst by supporting native controls, multiple windows, sharing, printing, menus and keyboard shortcuts.

