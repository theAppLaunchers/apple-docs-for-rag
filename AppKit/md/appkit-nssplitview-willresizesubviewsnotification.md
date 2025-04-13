

- AppKit
- NSSplitView
-  willResizeSubviewsNotification 

Type Property

# willResizeSubviewsNotification

A notification that posts before a change to the size of some or all subviews of a split view.

macOS

``` source
class let willResizeSubviewsNotification: NSNotification.Name
```

## Discussion

The notification object consists of the NSSplitView object about to resize its subviews.

The userInfo dictionary includes the `NSSplitViewDividerIndex` key that contains the index of the divider that the split view or the user moves. If the system sends the notification because the user drags a divider, the dictionary also includes the `NSSplitViewUserResizeKey` key with a value of `1`.

## See Also

### Managing Notifications

class let didResizeSubviewsNotification: NSNotification.Name

A notification that posts after a change to the size of some or all subviews of a split view.

