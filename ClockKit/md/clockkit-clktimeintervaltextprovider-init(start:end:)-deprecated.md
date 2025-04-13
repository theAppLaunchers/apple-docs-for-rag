

- ClockKit
- CLKTimeIntervalTextProvider
-  init(start:end:) Deprecated

Initializer

# init(start:end:)

Creates and returns a text provider with the specified start and end dates.

watchOS 2.0–9.0Deprecated

``` source
convenience init(
    start startDate: Date,
    end endDate: Date
)
```

Deprecated

On watchOS 9.0 or later, use WidgetKit instead

## Parameters 

`startDate`  

The start date for the time range. This parameter must not be `nil`.

`endDate`  

The end date for the time range. The specified date must come after the date in the `startDate` parameter. This parameter must not be `nil`.

## Return Value

A text provider initialized with the specified start and end dates.

## Discussion

The returned text provider uses the default calendar and time zone information for the current user. Date and time values are formatted according to the user’s current locale information.

## See Also

### Creating the Text Provider

convenience init(start: Date, end: Date, timeZone: TimeZone?)

Creates and returns a text provider with the specified dates and time zone information.

Deprecated

