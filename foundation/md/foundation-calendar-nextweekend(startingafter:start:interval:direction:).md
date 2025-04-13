

- Foundation
- Calendar
-  nextWeekend(startingAfter:start:interval:direction:) 

Instance Method

# nextWeekend(startingAfter:start:interval:direction:)

Returns the range of the next weekend via two inout parameters. The weekend starts strictly after the given date.

iOS 8.0+iPadOS 8.0+Mac Catalyst 8.0+macOS 10.10+tvOS 9.0+visionOS 1.0+watchOS 2.0+

``` source
func nextWeekend(
    startingAfter date: Date,
    start: inout Date,
    interval: inout TimeInterval,
    direction: Calendar.SearchDirection = .forward
) -> Bool
```

## Parameters 

`date`  

The date at which to begin the search.

`start`  

Upon return, the starting time of the calendar component that contains the date.

`interval`  

Upon return, the duration of the calendar component that contains the date.

`direction`  

Which direction in time to search. The default value is `.forward`.

## Return Value

`false` if the calendar and locale do not have the concept of a weekend, otherwise `true`.

## Discussion

If `direction` is `.backward`, then finds the previous weekend range strictly before the given date.

Note that a given entire day within a calendar is not necessarily all in a weekend or not; weekends can start in the middle of a day in some calendars and locales.

## See Also

### Calculating Intervals

func dateInterval(of: Calendar.Component, for: Date) -> DateInterval?

Returns the starting time and duration of a given calendar component that contains a given date.

func dateInterval(of: Calendar.Component, start: inout Date, interval: inout TimeInterval, for: Date) -> Bool

Returns, via two inout parameters, the starting time and duration of a given calendar component that contains a given date.

func dateIntervalOfWeekend(containing: Date) -> DateInterval?

Returns a `DateInterval` of the weekend contained by the given date, or `nil` if the date is not in a weekend.

func dateIntervalOfWeekend(containing: Date, start: inout Date, interval: inout TimeInterval) -> Bool

Find the range of the weekend around the given date, returned via two by-reference parameters.

func nextWeekend(startingAfter: Date, direction: Calendar.SearchDirection) -> DateInterval?

Returns a `DateInterval` of the next weekend, which starts strictly after the given date.

enum SearchDirection

The direction in time to search.

