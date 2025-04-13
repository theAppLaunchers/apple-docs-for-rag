

- UIKit
-  UIPrinter 

Class

# UIPrinter

A printer on the network.

iOS 8.0+iPadOS 8.0+Mac Catalyst 13.1+visionOS 1.0+

``` source
@MainActor
class UIPrinter
```

## Overview

You use a printer object to obtain information about a printer so that you can display that information in your app’s interface. You do not use printer objects to communicate with the printer directly.

Most of the time, you use a UIPrinterPickerController object to retrieve a printer object representing the printer selected by the user. If you already have a URL containing the address of a printer—perhaps one that was previously selected by the user—you can use that URL to create a printer object directly. When creating your own printer objects, you must connect to the printer using the contactPrinter(_:) method before retrieving any of the printer’s attributes.

## Topics

### Creating a printer object

init(url: URL)

Creates and returns a printer with the specified location.

### Getting the printer’s address

var url: URL

The full address of the printer.

### Getting the printer information

var displayName: String

The human-readable printer name.

var displayLocation: String?

The human-readable text that describes the location of the printer.

var makeAndModel: String?

A string that contains the manufacturer’s name and the model name of the printer.

var supportedJobTypes: UIPrinter.JobTypes

The capabilities of the printer.

struct JobTypes

Constants that indicate the types of jobs that the printer supports.

var supportsColor: Bool

A Boolean value that indicates whether the printer supports color printing.

var supportsDuplex: Bool

A Boolean value that indicates whether the printer supports printing on both sides of a sheet of paper.

### Connecting to the printer

func contactPrinter(((Bool) -> Void)?)

Connects to the printer and gathers information about its capabilities.

### Constants

enum CutterBehavior

Constants that specify the cutter behavior of a roll-fed printer.

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

### Job info

class UIPrintInfo

Information about a print job that the system uses when it prints.

class UIPrintPaper

The size of paper for a print job and the rectangular area that the content prints within.

