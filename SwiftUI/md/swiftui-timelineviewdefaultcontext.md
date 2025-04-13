

- SwiftUI
-  TimelineViewDefaultContext 

Type Alias

# TimelineViewDefaultContext

Information passed to a timeline view’s content callback.

iOS 15.0+iPadOS 15.0+Mac Catalyst 15.0+macOS 12.0+tvOS 15.0+visionOS 1.0+watchOS 8.0+

``` source
typealias TimelineViewDefaultContext = TimelineView.Context
```

## Discussion

The context includes both the date from the schedule that triggered the callback, and a cadence that you can use to customize the appearance of your view. For example, you might choose to display the second hand of an analog clock only when the cadence is TimelineView.Context.Cadence.seconds or faster.

Note

This type alias uses a specific concrete instance of TimelineView.Context that all timeline views can use. It does this to prevent introducing an unnecessary generic parameter dependency on the context type.

## See Also

### Updating a view on a schedule

Updating watchOS apps with timelines

Seamlessly schedule updates to your user interface, even while it’s inactive.

struct TimelineView

A view that updates according to a schedule that you provide.

protocol TimelineSchedule

A type that provides a sequence of dates for use as a schedule.

