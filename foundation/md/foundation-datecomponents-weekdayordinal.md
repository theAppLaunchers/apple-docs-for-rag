

- Foundation
- DateComponents
-  weekdayOrdinal 

Instance Property

# weekdayOrdinal

A weekday ordinal or count of weekday ordinals.

iOS 8.0+iPadOS 8.0+Mac Catalyst 8.0+macOS 10.9+tvOS 9.0+visionOS 1.0+watchOS 2.0+

``` source
var weekdayOrdinal: Int? { get set }
```

## Discussion

Weekday ordinal units represent the position of the weekday within the next larger calendar unit, such as the month. For example, 2 is the weekday ordinal unit for the second Friday of the month.

Note

This value is interpreted in the context of the calendar in which it is used.

## See Also

### Accessing Weeks and Days

var weekOfMonth: Int?

A week of the month or a count of weeks of the month.

var weekOfYear: Int?

A week of the year or count of the weeks of the year.

var weekday: Int?

A weekday or count of weekdays.

var day: Int?

A day or count of days.

