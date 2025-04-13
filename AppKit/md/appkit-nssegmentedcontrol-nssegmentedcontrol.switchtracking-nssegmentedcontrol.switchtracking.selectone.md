

- AppKit
- NSSegmentedControl
- NSSegmentedControl.SwitchTracking
-  NSSegmentedControl.SwitchTracking.selectOne 

Case

# NSSegmentedControl.SwitchTracking.selectOne

Only one segment in the control can be selected at a time.

macOS

``` source
case selectOne
```

## Discussion

This mode functions as a radio button and is illustrated by the view selection control in Finder, which allows you to toggle between icon view, list view, column view, and Cover Flow.

## See Also

### Constants

case selectAny

One or more segment cells in the control can be selected at a time.

case momentary

A segment is selected only when the user is pressing the mouse down within the bounds of the segment. When the mouse is no longer down within the segment, the segment is automatically deselected. A momentary segmented control sends an action when the user clicks a segment, and another action when the user releases the segment. If configured as continuous (see isContinuous), the control also sends actions at repeating intervals until the user releases the segment, at which point the control sends its final action.

case momentaryAccelerator

On pressure-sensitive systems, when the user force clicks a segment, a momentary accelerator segmented control sends repeating actions as pressure changes occur. The control stops sending actions when the user releases pressure. A document-based app, for example, might implement a momentary accelerator segmented control in order to allow a user to adjust the speed of paging by using variable pressure. In this example, actions are sent to the app to indicate when pressure on the control has changed. The app then determines the amount of pressure currently applied, and adjusts navigation speed accordingly.

