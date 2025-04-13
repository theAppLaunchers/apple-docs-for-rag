

- Core Foundation
- CFUserNotification
-  Response Codes 

API Collection

# Response Codes

Response codes identifying the button that was pressed to dismiss a notification dialog.

## Overview

To extract this value from the response flags of a dismissed notification (such as returned by CFUserNotificationReceiveResponse(_:_:_:)), you must perform a bitwise-AND operation between the returned response flags and `0x3` before comparing the value to these constants.

## Topics

### Constants

var kCFUserNotificationDefaultResponse: CFOptionFlags

The default button was pressed.

var kCFUserNotificationAlternateResponse: CFOptionFlags

The alternate button was pressed.

var kCFUserNotificationOtherResponse: CFOptionFlags

The third button was pressed.

var kCFUserNotificationCancelResponse: CFOptionFlags

No button was pressed and the notification timed out.

## See Also

### Constants

Alert Levels

Flags identifying the seriousness of a user notification.

Button Flags

Flags that alter the display of buttons in a user notification dialog.

Alert Levels

Flags identifying the seriousness of a user notification.

Button Flags

Flags that alter the display of buttons in a user notification dialog.

Dialog Description Keys

Keys used in a user notification’s description dictionary, which describes the contents of the notification dialog to display.

