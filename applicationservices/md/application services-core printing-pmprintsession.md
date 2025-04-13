

- Application Services
- Core Printing
-  PMPrintSession 

Type Alias

# PMPrintSession

An opaque type that stores information about a print job.

macOS 10.0+

``` source
typealias PMPrintSession = OpaquePointer
```

## Discussion

A printing session object contains information that’s needed by the page format and print settings objects, such as default page format and print settings values. For this reason, some printing functions can be called only after you have created a printing session object. For example, setting defaults for or validating page format and print settings objects can only be done after you have created a printing session object. Your application creates a printing session object using the function PMCreateSession(_:).

You can use a printing session to implement multithreaded printing, and you can create multiple sessions within a single-threaded application. If your application does not use sheets, then your application can open only one dialog at a time. Each printing session can have its own dialog, and settings changed in one dialog are independent of settings in any other dialog.

