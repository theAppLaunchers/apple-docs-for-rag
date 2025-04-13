

- Foundation
- Calendar
-  identifier 

Instance Property

# identifier

The identifier of the calendar.

iOS 8.0+iPadOS 8.0+Mac Catalyst 8.0+macOS 10.10+tvOS 9.0+visionOS 1.0+watchOS 2.0+

``` source
var identifier: Calendar.Identifier { get }
```

## See Also

### Getting Calendar Information

var locale: Locale?

The locale of the calendar.

var firstWeekday: Int

The first day of the week for the calendar.

var minimumDaysInFirstWeek: Int

The number of minimum days in the first week.

var timeZone: TimeZone

The time zone of the calendar.

func maximumRange(of: Calendar.Component) -> Range&lt;Int>?

The maximum range limits of the values that a given component can take on.

func minimumRange(of: Calendar.Component) -> Range&lt;Int>?

Returns the minimum range limits of the values that a given component can take on.

func ordinality(of: Calendar.Component, in: Calendar.Component, for: Date) -> Int?

Returns, for a given absolute time, the ordinal number of a smaller calendar component (such as a day) within a specified larger calendar component (such as a week).

func range(of: Calendar.Component, in: Calendar.Component, for: Date) -> Range&lt;Int>?

Returns the range of absolute time values that a smaller calendar component (such as a day) can take on in a larger calendar component (such as a month) that includes a specified absolute time.

