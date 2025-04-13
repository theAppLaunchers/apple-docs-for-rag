

- Foundation
- Calendar
-  shortQuarterSymbols 

Instance Property

# shortQuarterSymbols

A list of shorter-named quarters in this calendar, localized to the Calendar’s `locale`.

iOS 8.0+iPadOS 8.0+Mac Catalyst 8.0+macOS 10.10+tvOS 9.0+visionOS 1.0+watchOS 2.0+

``` source
var shortQuarterSymbols: [String] { get }
```

## Discussion

For example, for English in the Gregorian calendar, returns `["Q1", "Q2", "Q3", "Q4"]`.

Note

By default, Calendars have no locale set. If you wish to receive a localized answer, be sure to set the `locale` property first - most likely to `Locale.autoupdatingCurrent`.

## See Also

### Getting Quarter Symbols

var quarterSymbols: [String]

A list of quarter names in this calendar, localized to the Calendar’s `locale`.

var standaloneQuarterSymbols: [String]

A list of standalone quarter names in this calendar, localized to the Calendar’s `locale`.

var shortStandaloneQuarterSymbols: [String]

A list of shorter-named standalone quarters in this calendar, localized to the Calendar’s `locale`.

