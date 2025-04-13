

- Core Graphics
- CGPDFDocument
-  allowsPrinting 

Instance Property

# allowsPrinting

Returns whether a PDF document allows printing.

iOS 2.0+iPadOS 2.0+Mac Catalyst 13.1+macOS 10.2+tvOSvisionOS 1.0+watchOS 2.0+

``` source
var allowsPrinting: Bool { get }
```

## Discussion

If the document is encrypted and the current password doesn’t grant permission to perform printing, this returns false.

## See Also

### Working with an Encrypted PDF Document

var isEncrypted: Bool

Returns whether the specified PDF file is encrypted.

var allowsCopying: Bool

Returns whether the specified PDF document allows copying.

var isUnlocked: Bool

Returns whether the specified PDF document is currently unlocked.

func unlockWithPassword(UnsafePointer&lt;CChar>) -> Bool

Unlocks an encrypted PDF document when a valid password is supplied.

