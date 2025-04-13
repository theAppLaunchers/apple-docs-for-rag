

- UIKit
- UIPrinter
-  url 

Instance Property

# url

The full address of the printer.

iOS 8.0+iPadOS 8.0+Mac Catalyst 13.1+visionOS 1.0+

``` source
@MainActor
var url: URL { get }
```

## Discussion

Use this property to retrieve the address of a printer on the network. You can also save the value in this property to disk and use it later to initialize a new printer object that points to the same printer.

