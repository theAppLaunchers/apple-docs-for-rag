

- Foundation
- NSCalendar
- NSCalendar.Options
-  matchFirst 

Type Property

# matchFirst

Specifies that, if there are two or more matching times, the operation should return the first occurrence.

iOS 7.0+iPadOS 7.0+Mac Catalyst 13.1+macOS 10.9+tvOS 9.0+visionOS 1.0+watchOS 2.0+

``` source
static var matchFirst: NSCalendar.Options { get }
```

## See Also

### Constants

static var wrapComponents: NSCalendar.Options

Specifies that the components specified for an `NSDateComponents` object should be incremented and wrap around to zero/one on overflow, but should not cause higher units to be incremented.

static var matchStrictly: NSCalendar.Options

Specifies that the operation should travel as far forward or backward as necessary looking for a match.

static var searchBackwards: NSCalendar.Options

Specifies that the operation should travel backwards to find the previous match before the given date.

static var matchPreviousTimePreservingSmallerUnits: NSCalendar.Options

Specifies that, when there is no matching time before the end of the next instance of the next highest unit specified in the given `NSDateComponents` object, this method uses the *previous* existing value of the missing unit and preserves the lower units’ values.

static var matchNextTimePreservingSmallerUnits: NSCalendar.Options

Specifies that, when there is no matching time before the end of the next instance of the next highest unit specified in the given `NSDateComponents` object, this method uses the *next* existing value of the missing unit and preserves the lower units’ values.

static var matchNextTime: NSCalendar.Options

Specifies that, when there is no matching time before the end of the next instance of the next highest unit specified in the given `NSDateComponents` object, this method uses the *next* existing value of the missing unit and *does not* preserve the lower units’ values.

static var matchLast: NSCalendar.Options

Specifies that, if there are two or more matching times, the operation should return the last occurrence.

static var wrapComponents: NSCalendar.Options

Specifies that the components specified for an `NSDateComponents` object should be incremented and wrap around to zero/one on overflow, but should not cause higher units to be incremented.

static var matchStrictly: NSCalendar.Options

Specifies that the operation should travel as far forward or backward as necessary looking for a match.

static var searchBackwards: NSCalendar.Options

Specifies that the operation should travel backwards to find the previous match before the given date.

static var matchPreviousTimePreservingSmallerUnits: NSCalendar.Options

Specifies that, when there is no matching time before the end of the next instance of the next highest unit specified in the given `NSDateComponents` object, this method uses the *previous* existing value of the missing unit and preserves the lower units’ values.

static var matchNextTimePreservingSmallerUnits: NSCalendar.Options

Specifies that, when there is no matching time before the end of the next instance of the next highest unit specified in the given `NSDateComponents` object, this method uses the *next* existing value of the missing unit and preserves the lower units’ values.

static var matchNextTime: NSCalendar.Options

Specifies that, when there is no matching time before the end of the next instance of the next highest unit specified in the given `NSDateComponents` object, this method uses the *next* existing value of the missing unit and *does not* preserve the lower units’ values.

static var matchLast: NSCalendar.Options

Specifies that, if there are two or more matching times, the operation should return the last occurrence.

var NSWrapCalendarComponents: Int

Specifies that the components specified for an `NSDateComponents` object should be incremented and wrap around to zero/one on overflow, but should not cause higher units to be incremented.

Deprecated

