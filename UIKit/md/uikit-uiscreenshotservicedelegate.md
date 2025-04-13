

- UIKit
-  UIScreenshotServiceDelegate 

Protocol

# UIScreenshotServiceDelegate

Methods you use to generate PDF data that accompanies a user-requested screenshot.

iOSiPadOSMac CatalysttvOS

``` source
@MainActor
protocol UIScreenshotServiceDelegate : NSObjectProtocol
```

## Overview

When the user captures a screenshot of your app’s windows, UIKit calls the methods of this protocol to retrieve PDF data for those windows, and then it provides that data to the user. Adopt this protocol in a custom object of your app, and assign that object to the UIScreenshotService object associated with one of your window scenes. Use your custom delegate object to generate PDF content for the windows in the associated window-scene object.

## Topics

### Providing the PDF data

func screenshotService(UIScreenshotService, generatePDFRepresentationWithCompletion: (Data?, Int, CGRect) -> Void)

Generates a high-fidelity PDF version of the entire content in a given window scene.

## Relationships

### Inherits From

- NSObjectProtocol

## See Also

### Responding to screenshot requests

var delegate: (any UIScreenshotServiceDelegate)?

The custom object you use to provide PDF data for a screenshot.

