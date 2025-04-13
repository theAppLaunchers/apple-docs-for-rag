

- Foundation
- Calendar
-  standaloneQuarterSymbols 

Instance Property

# standaloneQuarterSymbols

A list of standalone quarter names in this calendar, localized to the Calendar’s `locale`.

iOS 8.0+iPadOS 8.0+Mac Catalyst 8.0+macOS 10.10+tvOS 9.0+visionOS 1.0+watchOS 2.0+

``` source
var standaloneQuarterSymbols: [String] { get }
```

## Discussion

For example, for English in the Gregorian calendar, returns `["1st quarter", "2nd quarter", "3rd quarter", "4th quarter"]`.

Note

Stand-alone properties are for use in places like calendar headers. Non-stand-alone properties are for use in context (for example, “Saturday, November 12th”).

Note

By default, Calendars have no locale set. If you wish to receive a localized answer, be sure to set the `locale` property first - most likely to `Locale.autoupdatingCurrent`.

## See Also

### Getting Quarter Symbols

var quarterSymbols: [String]

A list of quarter names in this calendar, localized to the Calendar’s `locale`.

var shortQuarterSymbols: [String]

A list of shorter-named quarters in this calendar, localized to the Calendar’s `locale`.

var shortStandaloneQuarterSymbols: [String]

A list of shorter-named standalone quarters in this calendar, localized to the Calendar’s `locale`.

