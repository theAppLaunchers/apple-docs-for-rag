

- Foundation
- DateIntervalFormatter
- DateIntervalFormatter.Style
-  DateIntervalFormatter.Style.full 

Case

# DateIntervalFormatter.Style.full

A fully spelled out date or time format.

iOS 8.0+iPadOS 8.0+Mac Catalyst 13.1+macOS 10.10+tvOS 9.0+visionOS 1.0+watchOS 2.0+

``` source
case full
```

## Discussion

For dates, this style displays the numerical day and year and a spelled out version of the month and day of week using a format appropriate for the current locale. For example, formatting the date January 15, 2015 with this style results in the value “Thursday, January 15, 2015” for US English and the value “Donnerstag, 15. Januar 2015” for German.

For times, this style displays hours, minutes, seconds, and the spelled-out time zone information using a format appropriate for the current locale. For example, 12 hours, 33 minutes, and 29 seconds in the afternoon using a 12-hour clock and the Pacific Time Zone results in the value “12:33:29 PM Pacific Standard Time” for US English without daylight savings in effect and “12:33:29 Nordamerikanische Westküsten-Normalzeit” for German.

## See Also

### Constants

case none

No information for the date or time. Use this style when you do not want to include date or time information in the resulting string.

case short

An abbreviated date or time format.

case medium

A medium length date or time format.

case long

A long length date or time format.

case none

No information for the date or time. Use this style when you do not want to include date or time information in the resulting string.

case short

An abbreviated date or time format.

case medium

A medium length date or time format.

case long

A long length date or time format.

