

- Foundation
- ByteCountFormatStyle
-  includesActualByteCount 

Instance Property

# includesActualByteCount

A Boolean value that indicates whether the format style should include the exact byte count, in addition to expressing it in terms of units.

iOS 15.0+iPadOS 15.0+Mac Catalyst 15.0+macOS 12.0+tvOS 15.0+visionOS 1.0+watchOS 8.0+

``` source
var includesActualByteCount: Bool { get set }
```

## Discussion

When this value is `true`, a format style produces output like `1 kB (1,024 bytes)`.

## See Also

### Accessing style properties

var allowedUnits: ByteCountFormatStyle.Units

The units the format style can use to express the byte count.

struct Units

The units to use when formatting a byte count, such as kilobytes or gigabytes.

var spellsOutZero: Bool

A Boolean value that indicates whether the format style should spell out zero-byte values as text.

var locale: Locale

The locale to use to format the numeric part of the byte count.

