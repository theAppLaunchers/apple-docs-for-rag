

- WebKit
- WKWebExtension
-  errors 

Instance Property

# errors

An array of all errors that occurred during the processing of the extension.

iOS 18.4+iPadOS 18.4+Mac Catalyst 18.4+macOS 15.4+visionOS 2.4+

``` source
@MainActor
var errors: [any Error] { get }
```

## Discussion

Provides an array of all parse-time errors for the extension, with repeat errors consolidated into a single entry for the original occurrence only. If no errors occurred, an empty array is returned.

Note

Once the extension is loaded, use the errors property on an extension context to monitor any runtime errors, as they can occur after the extension is loaded.

