

- Core Foundation
-  CFCalendarGetOrdinalityOfUnit(\_:\_:\_:\_:) 

Function

# CFCalendarGetOrdinalityOfUnit(\_:\_:\_:\_:)

Returns the ordinal number of a calendrical unit within a larger unit at a specified absolute time.

iOSiPadOSMac CatalystmacOStvOSvisionOSwatchOS

``` source
func CFCalendarGetOrdinalityOfUnit(
    _ calendar: CFCalendar!,
    _ smallerUnit: CFCalendarUnit,
    _ biggerUnit: CFCalendarUnit,
    _ at: CFAbsoluteTime
) -> CFIndex
```

## Parameters 

`calendar`  

The calendar to examine.

`smallerUnit`  

A calendar unit. For valid values see CFCalendarUnit.

`biggerUnit`  

A calendar unit. For valid values see CFCalendarUnit.

`at`  

An absolute time.

## Return Value

The ordinal number of the calendar unit specified by `smallerUnit` within the calendar unit specified by `biggerUnit` at the absolute time `at`. For example, the time 00:45 is in the first hour of the day, and for units Hour and Day respectively, the result would be 1.

## Discussion

If the `biggerUnit` parameter is not logically bigger than the `smallerUnit` parameter in the calendar, or the given combination of units does not make sense (or is a computation which is undefined), the result is `kCFNotFound`.

## Discussion

The ordinality is in most cases not the same as the decomposed value of the unit. Typically return values are `1` and greater; an exception is the week-in-month calculation, which returns `0` for days before the first week in the month containing the date. Note that some computations can take a relatively long time to perform.

## See Also

### Getting Ranges of Units

func CFCalendarGetRangeOfUnit(CFCalendar!, CFCalendarUnit, CFCalendarUnit, CFAbsoluteTime) -> CFRange

Returns the range of values that one unit can take on within a larger unit during which a specific absolute time occurs.

func CFCalendarGetTimeRangeOfUnit(CFCalendar!, CFCalendarUnit, CFAbsoluteTime, UnsafeMutablePointer&lt;CFAbsoluteTime>!, UnsafeMutablePointer&lt;CFTimeInterval>!) -> Bool

Returns by reference the start time and duration of a given calendar unit that contains a given absolute time.

func CFCalendarGetMaximumRangeOfUnit(CFCalendar!, CFCalendarUnit) -> CFRange

Returns the maximum range limits of the values that a specified unit can take on in a given calendar.

func CFCalendarGetMinimumRangeOfUnit(CFCalendar!, CFCalendarUnit) -> CFRange

Returns the minimum range limits of the values that a specified unit can take on in a given calendar.

