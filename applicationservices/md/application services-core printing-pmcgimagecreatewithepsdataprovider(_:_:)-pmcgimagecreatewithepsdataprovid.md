

- Application Services
- Core Printing
-  PMCGImageCreateWithEPSDataProvider(\_:\_:) 

Function

# PMCGImageCreateWithEPSDataProvider(\_:\_:)

Creates an image that references both the PostScript contents of EPS data and a preview (proxy) image for the data.

macOS 10.1+

``` source
func PMCGImageCreateWithEPSDataProvider(
    _ epsDataProvider: CGDataProvider?,
    _ epsPreview: CGImage
) -> Unmanaged?
```

## Parameters 

`epsDataProvider`  

A Quartz data provider that supplies the PostScript contents of the EPS file. The EPS data must begin with the EPSF required header and bounding box DSC (Document Structuring Conventions) comments.

`epsPreview`  

A Quartz image that serves as the proxy image for the EPS file. When the image returned by this function is rendered onscreen or sent to a printer that cannot render PostScript, this proxy image is drawn instead.

## Return Value

An image capable of rendering either the EPS content or the proxy image, depending upon the capabilities of the destination printer.

## Discussion

It is likely that data will not be read from the EPS data provider until after this function returns. You should be careful not to free the underlying EPS data until the data provider's release function is invoked. Similarly, do not free the preview image data until the image data provider's release function is invoked. You are responsible for releasing the data providers for the EPS image and the EPS preview image.

Note that in macOS 10.3 and later, Quartz can convert EPS data into PDF data. Using this feature and then using Quartz to draw the resulting PDF data may produce superior results for your application. See `CGPSConverter` for details.

## See Also

### Printing with PostScript Data

func PMPrinterWritePostScriptToURL(PMPrinter, PMPrintSettings, PMPageFormat?, CFString?, CFURL, CFURL) -> OSStatus

Converts an input file of the specified MIME type to printer-ready PostScript for a destination printer.

