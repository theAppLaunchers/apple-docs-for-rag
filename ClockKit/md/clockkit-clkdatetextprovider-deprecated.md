

- ClockKit
-  CLKDateTextProvider Deprecated

Class

# CLKDateTextProvider

A formatted string that conveys a date without any time information.

watchOS 2.0–9.0Deprecated

``` source
class CLKDateTextProvider
```

Deprecated

Use WidgetKit to create complications for watchOS 10 or later. For more information, see Migrating to WidgetKit.

## Mentioned in 

Creating a timeline entry

## Overview

Use a date provider for strings that contain day, month, and year information. The text provider formats the date information consistently and in a way that makes the best use of the available space. It also takes into account the user’s region and locale settings.

When creating the formatted string, the date text provider creates the longest string that fits in the given space. It includes as many of the requested date elements as it can, but may truncate elements or use abbreviations as needed.

### Date Format Options

When creating a `CLKDateTextProvider` object, you must specify which calendar units you want included in the resulting date. Only the following calendar units are supported:

- NSDayCalendarUnit

- NSMonthCalendarUnit

- NSWeekdayCalendarUnit

- NSYearCalendarUnit

All other calendar units are ignored.

When formatting the date, the date text provider drops units starting at the end of the preceding list and working up. In other words, it drops the year first, followed by the weekday information, followed by the month. For example, a text provider configured to display all units for the date December 28, 2014 in the English-US locale would remove elements as follows until it encountered a string that fit the available space:

- `Saturday, December 28, 2015`

- `Saturday, December 28`

- `Saturday, Dec 28`

- `Sat, Dec 28`

- `Dec 28`

- `28`

## Topics

### Creating a Text Provider

convenience init(date: Date, units: NSCalendar.Unit)

Creates and returns a text provider with the specified date and the default time zone.

convenience init(date: Date, units: NSCalendar.Unit, timeZone: TimeZone?)

Creates and returns a text provider with the specified date and time zone.

### Getting the Date Information

var date: Date

The date to display.

var timeZone: TimeZone?

The time zone used in the formatted string.

var calendarUnits: NSCalendar.Unit

The calendar units to include in the formatted string.

var uppercase: Bool

A Boolean value that determines whether the date string displays in uppercase.

## Relationships

### Inherits From

- CLKTextProvider

### Conforms To

- CVarArg
- CustomDebugStringConvertible
- CustomStringConvertible
- Equatable
- Hashable
- NSCopying
- NSObjectProtocol

## See Also

### Text providers

class CLKSimpleTextProvider

A single line of text to display in your complication interface.

Deprecated

class CLKRelativeDateTextProvider

A formatted string that conveys the difference in time between the current date and a date that you specify.

Deprecated

class CLKTimeIntervalTextProvider

A formatted time range.

Deprecated

class CLKTimeTextProvider

A formatted time value.

Deprecated

class CLKTextProvider

The common behavior for displaying text-based data in a complication.

Deprecated

