

- Foundation
- NSCalendar
-  date(bySettingHour:minute:second:of:options:) 

Instance Method

# date(bySettingHour:minute:second:of:options:)

Creates a new date calculated with the given time.

iOS 8.0+iPadOS 8.0+Mac Catalyst 13.1+macOS 10.9+tvOS 9.0+visionOS 1.0+watchOS 2.0+

``` source
func date(
    bySettingHour h: Int,
    minute m: Int,
    second s: Int,
    of date: Date,
    options opts: NSCalendar.Options = []
) -> Date?
```

## Parameters 

`h`  

The hour value.

`m`  

The minute value.

`s`  

The second value.

`date`  

The date to use to perform the calculation.

`opts`  

Options for the calculation. For possible values, see NSCalendar.Options.

## Return Value

A new `NSDate` instance representing the date calculated by setting the given hour, minute, and second, to a given time. If no such time exists for the specified components, the next available date is returned, which may be on a different calendar day.

## Discussion

You can use this method to calculate a date at a different time of a particular calendar day.

## See Also

### Calculating Dates

func date(from: DateComponents) -> Date?

Returns a date representing the absolute time calculated from given components.

func date(byAdding: DateComponents, to: Date, options: NSCalendar.Options) -> Date?

Returns a date representing the absolute time calculated by adding given components to a given date.

func date(byAdding: NSCalendar.Unit, value: Int, to: Date, options: NSCalendar.Options) -> Date?

Returns a date representing the absolute time calculated by adding the value of a given component to a given date.

func date(bySettingUnit: NSCalendar.Unit, value: Int, of: Date, options: NSCalendar.Options) -> Date?

Returns a new date representing the date calculated by setting a specific component of a given date to a given value, while trying to keep lower components the same.

func date(era: Int, year: Int, month: Int, day: Int, hour: Int, minute: Int, second: Int, nanosecond: Int) -> Date?

Returns a date created with the given components.

func date(era: Int, yearForWeekOfYear: Int, weekOfYear: Int, weekday: Int, hour: Int, minute: Int, second: Int, nanosecond: Int) -> Date?

Returns a new date created with the given components base on a week-of-year value.

func nextWeekendStart(AutoreleasingUnsafeMutablePointer&lt;NSDate?>?, interval: UnsafeMutablePointer&lt;TimeInterval>?, options: NSCalendar.Options, after: Date) -> Bool

Returns by reference the starting date and time interval range of the next weekend period after a given date.

