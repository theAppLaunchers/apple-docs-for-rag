

- Core Image
- Generator Filters
-  pdf417BarcodeGenerator() 

Type Method

# pdf417BarcodeGenerator()

Generates a high-density linear barcode.

iOS 13.0+iPadOS 13.0+macOS 10.15+tvOS 13.0+visionOS 1.0+

``` source
class func pdf417BarcodeGenerator() -> any CIFilter & CIPDF417BarcodeGenerator
```

## Return Value

The generated image.

## Discussion

This method generates a PDF417 barcode as an image. PDF417 is a high-density stacked linear barcode format defined in the ISO 15438 standard. Use this filter to generate alphanumeric or numeric-only barcodes. Commonly used on identification cards or inventory management because of the large amount of data the barcode can hold.

The PDF417 barcode generator filter uses the following properties:

`message`  
An NSData object representing the data to be encoded as a barcode.

`minWidth`  
A `float` representing the minimum width of the barcode’s data area, in pixels as an `NSNumber`.

`maxWidth`  
A `float` representing the maximum width of the barcode’s data area, in pixels, as an `NSNumber`.

`maxHeight`  
A `float` representing the maximum height of the barcode’s data area, in pixels, as an `NSNumber`.

`minHeight`  
A `float` representing the minimum height of the barcode’s data area, in pixels, as an `NSNumber`.

`dataColums`  
A `float` representing the number of columns in the data area as an `NSNumber`.

`rows`  
A `float` representing the number of rows in the data area as an `NSNumber`.

`preferredAspectRatio`  
A `float` representing the desired aspect ratio as an `NSNumber`.

`compactionMode`  
An option that determines which method the generator uses to compress data as an `NSNumber`. See the note below for the possible values.

`compactStyle`  
A `Boolean` value of `0` or `1` that determines the omission of redundant elements to make the generated barcode more compact as an `NSNumber`.

`correctionLevel`  
A `float` between 0 and 8 that determines the amount of redundancy to include in the barcode’s data to prevent errors when the barcode is read. If left unspecified, the generator chooses a correction level based on the size of the message data.

`alwaysSpecifyCompaction`  
A `Boolean` value of `0` or `1` that determines the inclusion of information about the compaction mode in the barcode as an `NSNumber`. If a PDF417 barcode doesn’t contain compaction mode information, the reader assumes text-based compaction.

The `compactionMode` property takes one of the following numeric values:

| Value | Name | Description |
|----|----|----|
| `1` | Automatic | The generator automatically chooses a compression method. This option is the default. |
| `2` | Numeric | Valid only when the message is an ASCII-encoded string of digits, achieving optimal compression for that type of data. |
| `3` | Text | Valid only when the message is all ASCII-encoded alphanumeric and punctuation characters, achieving optimal compression for that type of data. |
| `4` | Byte | Valid for any data, but least compact. |

Select either 1 or the appropriate valid value for your data that gives the most compact output.

The following code creates a filter that generates a PDF417 barcode:

func pdf417Barcode(inputMessage: String) -> CIImage {
    let pdf417BarcodeGenerator = CIFilter.pdf417BarcodeGenerator()
    pdf417BarcodeGenerator.message = inputMessage.data(using: .ascii)!
    pdf417BarcodeGenerator.minWidth = 56
    pdf417BarcodeGenerator.maxWidth = 58
    pdf417BarcodeGenerator.maxHeight = 283
    pdf417BarcodeGenerator.minHeight = 13
    pdf417BarcodeGenerator.dataColumns = 9
    pdf417BarcodeGenerator.rows = 6
    pdf417BarcodeGenerator.preferredAspectRatio = 0.0
    pdf417BarcodeGenerator.compactionMode = 1
    pdf417BarcodeGenerator.compactStyle = 1
    pdf417BarcodeGenerator.correctionLevel = 0.01
    pdf417BarcodeGenerator.alwaysSpecifyCompaction = 0
    return pdf417BarcodeGenerator.outputImage!
}

## See Also

### Filters

class func attributedTextImageGenerator() -> any CIFilter &amp; CIAttributedTextImageGenerator

Generates an attributed-text image.

class func aztecCodeGenerator() -> any CIFilter &amp; CIAztecCodeGenerator

Generates a low-density barcode.

class func barcodeGenerator() -> any CIFilter &amp; CIBarcodeGenerator

Generates a barcode as an image from the descriptor.

class func blurredRectangleGenerator() -> any CIFilter &amp; CIBlurredRectangleGenerator

Generates a blurred rectangle.

class func checkerboardGenerator() -> any CIFilter &amp; CICheckerboardGenerator

Generates a checkerboard image.

class func code128BarcodeGenerator() -> any CIFilter &amp; CICode128BarcodeGenerator

Generates a high-density, linear barcode.

class func lenticularHaloGenerator() -> any CIFilter &amp; CILenticularHaloGenerator

Generates a lenticular halo image.

class func meshGenerator() -> any CIFilter &amp; CIMeshGenerator

Generates a pattern made from an array of line segments.

class func qrCodeGenerator() -> any CIFilter &amp; CIQRCodeGenerator

Generates a quick response (QR) code image.

class func randomGenerator() -> any CIFilter &amp; CIRandomGenerator

Generates a random filter image.

class func roundedRectangleGenerator() -> any CIFilter &amp; CIRoundedRectangleGenerator

Generates a rounded rectangle image.

class func roundedRectangleStrokeGenerator() -> any CIFilter &amp; CIRoundedRectangleStrokeGenerator

Creates an image containing the outline of a rounded rectangle.

class func starShineGenerator() -> any CIFilter &amp; CIStarShineGenerator

Generates a star-shine image.

class func stripesGenerator() -> any CIFilter &amp; CIStripesGenerator

Generates a line of stripes as an image

class func sunbeamsGenerator() -> any CIFilter &amp; CISunbeamsGenerator

Generates an image resembling the sun.

class func textImageGenerator() -> any CIFilter &amp; CITextImageGenerator

Generates a text image.

