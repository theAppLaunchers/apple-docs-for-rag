

- Core Foundation
- CFUserNotification
-  Dialog Description Keys 

API Collection

# Dialog Description Keys

Keys used in a user notification’s description dictionary, which describes the contents of the notification dialog to display.

## Overview

When creating the user notification with CFUserNotificationCreate(_:_:_:_:_:), the description dictionary must have a value for kCFUserNotificationAlertHeaderKey. All other keys are optional.

The button title keys must be given in right-to-left order—you therefore must use the `kCFUserNotificationDefaultButtonTitleKey` constant for the rightmost button even if it is conceptually not a “default” button (for example, if you want a single “Cancel” button that should not have color, should not pulse, and should not have return for a key equivalent). If, however, you set the `kCFUserNotificationNoDefaultButtonFlag`, the rightmost button does not behave as a default button (although it will still be the “default” button in the sense of using `kCFUserNotificationDefaultButtonTitleKey` and `kCFUserNotificationDefaultResponse`). The following code fragment shows how you can create a notification that contains a single “Cancel” button that does not behave as a default button.

```
const void* keys[] = {kCFUserNotificationAlertHeaderKey,
                      kCFUserNotificationProgressIndicatorValueKey,
                      kCFUserNotificationDefaultButtonTitleKey};
const void* values[] = {CFSTR("Progress"),
                        kCFBooleanTrue,
                        CFSTR("Cancel")};
CFDictionaryRef parameters = CFDictionaryCreate(0, keys, values,
        sizeof(keys)/sizeof(*keys), &kCFTypeDictionaryKeyCallBacks,
        &kCFTypeDictionaryValueCallBacks);
SInt32 err = 0;
CFUserNotificationCreate(kCFAllocatorDefault, 0,
        kCFUserNotificationPlainAlertLevel | kCFUserNotificationNoDefaultButtonFlag,
        &err, parameters);
```

If you set the `kCFUserNotificationNoDefaultButtonFlag` flag and do not specify a value for `kCFUserNotificationDefaultButtonTitleKey`, the notification will have no buttons.

## Topics

### Constants

let kCFUserNotificationIconURLKey: CFString!

A file URL pointing to the icon to display in the dialog.

let kCFUserNotificationSoundURLKey: CFString!

A file URL pointing to a sound that will be played when the alert appears.

let kCFUserNotificationLocalizationURLKey: CFString!

A file URL pointing to a bundle that contains localized versions of the strings displayed in the dialog.

let kCFUserNotificationAlertHeaderKey: CFString!

The title of the notification dialog.

let kCFUserNotificationAlertMessageKey: CFString!

The message string to display in the dialog.

let kCFUserNotificationDefaultButtonTitleKey: CFString!

The title of the default button.

let kCFUserNotificationAlternateButtonTitleKey: CFString!

The title of an optional alternate button.

let kCFUserNotificationOtherButtonTitleKey: CFString!

The title of an optional third button.

let kCFUserNotificationProgressIndicatorValueKey: CFString!

A value to indicate the progress of an operation.

let kCFUserNotificationPopUpTitlesKey: CFString!

The list of strings to display in a pop-up menu.

let kCFUserNotificationTextFieldTitlesKey: CFString!

The list of titles for all the text fields to display.

let kCFUserNotificationCheckBoxTitlesKey: CFString!

The list of titles for all the checkboxes or radio buttons to display.

let kCFUserNotificationTextFieldValuesKey: CFString!

The list of values to put into the text fields. If only one text field is to be displayed, you can pass its value string directly without putting it into an array first.

let kCFUserNotificationPopUpSelectionKey: CFString!

The item that was selected from a pop-up menu.

## See Also

### Constants

Alert Levels

Flags identifying the seriousness of a user notification.

Response Codes

Response codes identifying the button that was pressed to dismiss a notification dialog.

Button Flags

Flags that alter the display of buttons in a user notification dialog.

Alert Levels

Flags identifying the seriousness of a user notification.

Response Codes

Response codes identifying the button that was pressed to dismiss a notification dialog.

Button Flags

Flags that alter the display of buttons in a user notification dialog.

