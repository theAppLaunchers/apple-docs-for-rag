

- Foundation
- NSCalendar
-  date(from:) 

Instance Method

# date(from:)

Returns a date representing the absolute time calculated from given components.

iOS 2.0+iPadOS 2.0+Mac Catalyst 13.0+macOS 10.0+tvOS 9.0+visionOS 1.0+watchOS 2.0+

``` source
func date(from comps: DateComponents) -> Date?
```

## Parameters 

`comps`  

The components from which to calculate the returned date.

## Return Value

A new `NSDate` object representing the absolute time calculated from `comps`. Returns `nil` if the receiver cannot convert the components given in `comps` into an `NSDate` object.

## Discussion

When there are insufficient components provided to completely specify an absolute time, a calendar uses default values of its choice. When there is inconsistent information, a calendar may ignore some of the components parameters or the method may return `nil`. Unnecessary components are ignored (for example, Day takes precedence over Weekday and Weekday ordinals).

The following example shows how to use this method to create a date object to represent 14:10:00 on 6 January 1965, for a given calendar (`gregorian`).

```
NSDateComponents *comps = [[NSDateComponents alloc] init];
[comps setYear:1965];
[comps setMonth:1];
[comps setDay:6];
[comps setHour:14];
[comps setMinute:10];
[comps setSecond:0];
NSDate *date = [gregorian dateFromComponents:comps];
[comps release];
```

Note that some computations can take a relatively long time to perform.

## See Also

### Related Documentation

func components(NSCalendar.Unit, from: Date) -> DateComponents

Returns the date components representing a given date.

### Calculating Dates

func date(byAdding: DateComponents, to: Date, options: NSCalendar.Options) -> Date?

Returns a date representing the absolute time calculated by adding given components to a given date.

func date(byAdding: NSCalendar.Unit, value: Int, to: Date, options: NSCalendar.Options) -> Date?

Returns a date representing the absolute time calculated by adding the value of a given component to a given date.

func date(bySettingHour: Int, minute: Int, second: Int, of: Date, options: NSCalendar.Options) -> Date?

Creates a new date calculated with the given time.

func date(bySettingUnit: NSCalendar.Unit, value: Int, of: Date, options: NSCalendar.Options) -> Date?

Returns a new date representing the date calculated by setting a specific component of a given date to a given value, while trying to keep lower components the same.

func date(era: Int, year: Int, month: Int, day: Int, hour: Int, minute: Int, second: Int, nanosecond: Int) -> Date?

Returns a date created with the given components.

func date(era: Int, yearForWeekOfYear: Int, weekOfYear: Int, weekday: Int, hour: Int, minute: Int, second: Int, nanosecond: Int) -> Date?

Returns a new date created with the given components base on a week-of-year value.

func nextWeekendStart(AutoreleasingUnsafeMutablePointer&lt;NSDate?>?, interval: UnsafeMutablePointer&lt;TimeInterval>?, options: NSCalendar.Options, after: Date) -> Bool

Returns by reference the starting date and time interval range of the next weekend period after a given date.

