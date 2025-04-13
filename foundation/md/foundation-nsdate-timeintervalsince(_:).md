

- Foundation
- NSDate
-  timeIntervalSince(\_:) 

Instance Method

# timeIntervalSince(\_:)

Returns the interval between the receiver and another given date.

iOS 2.0+iPadOS 2.0+Mac Catalyst 13.0+macOS 10.0+tvOS 9.0+visionOS 1.0+watchOS 2.0+

``` source
func timeIntervalSince(_ anotherDate: Date) -> TimeInterval
```

## Parameters 

`anotherDate`  

The date with which to compare the receiver. You must pass a non-`nil` date object.

## Return Value

The interval between the receiver and the `anotherDate` parameter. If the receiver is earlier than `anotherDate`, the return value is negative. If `anotherDate` is `nil`, the results are undefined.

## See Also

### Getting Time Intervals

var timeIntervalSinceNow: TimeInterval

The interval between the date object and the current date and time.

var timeIntervalSinceReferenceDate: TimeInterval

The interval between the date object and 00:00:00 UTC on 1 January 2001.

var timeIntervalSince1970: TimeInterval

The interval between the date object and 00:00:00 UTC on 1 January 1970.

class var timeIntervalSinceReferenceDate: TimeInterval

The interval between 00:00:00 UTC on 1 January 2001 and the current date and time.

var NSTimeIntervalSince1970: Double

The number of seconds from 1 January 1970 to the reference date, 1 January 2001.

