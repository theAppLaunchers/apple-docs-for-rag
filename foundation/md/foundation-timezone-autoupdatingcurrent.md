

- Foundation
- TimeZone
-  autoupdatingCurrent 

Type Property

# autoupdatingCurrent

The time zone currently used by the system, automatically updating to the user’s current preference.

iOS 8.0+iPadOS 8.0+Mac Catalyst 8.0+macOS 10.10+tvOS 9.0+visionOS 1.0+watchOS 2.0+

``` source
static var autoupdatingCurrent: TimeZone { get }
```

## Discussion

If this time zone is mutated, then it no longer tracks the system time zone.

The autoupdating time zone only compares equal to itself.

## See Also

### Getting the Current Time Zone

static var current: TimeZone

The time zone currently used by the system.

