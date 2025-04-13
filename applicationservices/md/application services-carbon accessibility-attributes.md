

- Application Services
- Carbon Accessibility
-  Attributes 

API Collection

# Attributes

Define the attributes available for accessibility objects.

## Overview

See the “Roles and Associated Attributes” appendix in Accessibility Programming Guide for OS X for more information on which attributes are associated with a specific role.

## Topics

### Constants

var kAXRoleAttribute: String

The role, or type, of this accessibility object (for example, `AXButton`). This string is for identification purposes only and does not need to be localized. All accessibility objects must include this attribute.

var kAXSubroleAttribute: String

var kAXRoleDescriptionAttribute: String

var kAXHelpAttribute: String

A localized string containing help text for this accessibility object. An accessibility object that provides help information should include this attribute.

var kAXTitleAttribute: String

var kAXValueAttribute: String

var kAXMinValueAttribute: String

The minimum value this accessibility object can display (for example, the minimum value of a scroller control). This attribute is used only in conjunction with the `AXValue` attribute.

var kAXMaxValueAttribute: String

The maximum value this accessibility object can display (for example, the maximum value of a scroller control). This attribute is used only in conjunction with the `AXValue` attribute.

var kAXValueIncrementAttribute: String

The amount an accessibility object’s value changes as the result of a single action (for example, how far a scroller travels with one mouse click). This attribute is used only in conjunction with the `AXValue` attribute.

var kAXAllowedValuesAttribute: String

var kAXEnabledAttribute: String

var kAXFocusedAttribute: String

var kAXParentAttribute: String

This accessibility object’s parent object in the accessibility hierarchy. This attribute is required for all accessibility objects except the application-level accessibility object.

var kAXChildrenAttribute: String

var kAXSelectedChildrenAttribute: String

var kAXVisibleChildrenAttribute: String

var kAXWindowAttribute: String

var kAXPositionAttribute: String

var kAXTopLevelUIElementAttribute: String

var kAXSizeAttribute: String

The vertical and horizontal dimensions of this accessibility object. This attribute is required for all accessibility objects that are visible on the screen.

var kAXOrientationAttribute: String

var kAXDescriptionAttribute: String

var kAXSelectedTextAttribute: String

The currently selected text within this accessibility object. This attribute is required for all accessibility objects that represent editable text elements.

var kAXSelectedTextRangeAttribute: String

Indicates the range of characters (not bytes) that defines the currently selected text within this accessibility object. This attribute is required for all accessibility objects that represent editable text elements.

var kAXVisibleCharacterRangeAttribute: String

var kAXNumberOfCharactersAttribute: String

The total number of characters (not bytes) in the editable text element represented by this accessibility object. This attribute is required for all accessibility objects that represent editable text elements.

var kAXSharedTextUIElementsAttribute: String

var kAXSharedCharacterRangeAttribute: String

var kAXMainAttribute: String

var kAXMinimizedAttribute: String

Indicates whether the window represented by this accessibility object is currently minimized in the Dock. This attribute is recommended for all accessibility objects that represent windows that can be minimized.

var kAXCloseButtonAttribute: String

var kAXZoomButtonAttribute: String

var kAXMinimizeButtonAttribute: String

var kAXToolbarButtonAttribute: String

var kAXGrowAreaAttribute: String

var kAXProxyAttribute: String

var kAXModalAttribute: String

Indicates whether the window represented by this accessibility object is modal. This attribute is recommended for all accessibility objects that represent windows.

var kAXDefaultButtonAttribute: String

var kAXCancelButtonAttribute: String

var kAXMenuItemCmdCharAttribute: String

The primary key in the keyboard shortcut for the command represented by this accessibility object. For example, “O” is the primary key in the keyboard shortcut for the Open command.

var kAXMenuItemCmdVirtualKeyAttribute: String

var kAXMenuItemCmdGlyphAttribute: String

var kAXMenuItemCmdModifiersAttribute: String

An integer mask that represents the modifier keys held down in the keyboard shortcut for the command represented by this accessibility object.

var kAXMenuItemMarkCharAttribute: String

var kAXMenuItemPrimaryUIElementAttribute: String

var kAXMenuBarAttribute: String

var kAXWindowsAttribute: String

An array of accessibility objects representing this application’s windows. This attribute is recommended for all application-level accessibility objects.

var kAXFrontmostAttribute: String

Indicates whether the application represented by this accessibility object is active. This attribute is recommended for all application-level accessibility objects.

var kAXHiddenAttribute: String

Indicates whether the application represented by this accessibility object is hidden. This attribute is recommended for all application-level accessibility objects.

var kAXMainWindowAttribute: String

The accessibility object representing this application’s main window. This attribute is recommended for all application-level accessibility objects.

var kAXFocusedWindowAttribute: String

The accessibility object that represents the currently focused window of this application. This attribute is recommended for all application-level accessibility objects.

var kAXHeaderAttribute: String

var kAXEditedAttribute: String

var kAXTitleUIElementAttribute: String

An accessibility object that represents a static text title associated with another accessibility object.

var kAXValueWrapsAttribute: String

Indicates whether the value displayed in the user interface element represented by this accessibility object wraps around.

var kAXTabsAttribute: String

var kAXHorizontalScrollBarAttribute: String

var kAXVerticalScrollBarAttribute: String

var kAXOverflowButtonAttribute: String

Identifies which child of an accessibility object representing a toolbar is the overflow button (if any). This attribute is optional.

var kAXFilenameAttribute: String

The filename associated with this accessibility object. This attribute is optional.

var kAXExpandedAttribute: String

Indicates whether the menu displayed by the combo box or pop-up menu represented by this accessibility object is currently expanded. This attribute is recommended for all accessibility objects that display a pop-up menu.

var kAXSelectedAttribute: String

Indicates whether the row or column element represented by this accessibility object is selected. This attribute is recommended for all accessibility objects that represent selectable rows or columns.

var kAXSplittersAttribute: String

An array of views and splitter bar elements displayed by the split view represented by this accessibility object. This is a convenience attribute that helps an assistive application easily find these elements.

var kAXNextContentsAttribute: String

var kAXPreviousContentsAttribute: String

var kAXDocumentAttribute: String

The URL of the open document represented by this accessibility object. This attribute represents the URL as a string object.

var kAXIncrementButtonAttribute: String

var kAXDecrementButtonAttribute: String

The decrement element associated with the user interface object this accessibility object represents. This attribute can be used to provide convenient access to the decrement area of a custom user interface object.

var kAXContentsAttribute: String

var kAXIncrementorAttribute: String

The incrementor of a time or date field represented by this accessibility object. This attribute is required for accessibility objects that represent time or date field elements that display an incrementor.

var kAXHourFieldAttribute: String

The hour field of a time field represented by this accessibility object. This attribute is required for accessibility objects that represent time fields that display hours.

var kAXMinuteFieldAttribute: String

The minute field of a time field represented by this accessibility object. This attribute is required for accessibility objects that represent time fields that display minutes.

var kAXSecondFieldAttribute: String

The second field of a time field represented by this accessibility object. This attribute is required for accessibility objects that represent time fields that display seconds.

var kAXAMPMFieldAttribute: String

The AM/PM field of a time field represented by this accessibility object. This attribute is required for accessibility objects that represent time fields that display AM/PM settings.

var kAXDayFieldAttribute: String

The day field of a time field represented by this accessibility object. This attribute is required for accessibility objects that represent time fields that display days.

var kAXMonthFieldAttribute: String

The month field of a time field represented by this accessibility object. This attribute is required for accessibility objects that represent time fields that display months.

var kAXYearFieldAttribute: String

The year field of a time field represented by this accessibility object. This attribute is required for accessibility objects that represent time fields that display years.

var kAXColumnTitleAttribute: String

var kAXURLAttribute: String

The URL that describes the location of the document or application represented by this accessibility object.

var kAXLabelUIElementsAttribute: String

var kAXLabelValueAttribute: String

The value of the label represented by this accessibility object. This attribute is required for all accessibility objects that represent labels.

var kAXShownMenuUIElementAttribute: String

An array of accessibility objects that represent the contextual or Dock menus provided by this accessibility object.

var kAXServesAsTitleForUIElementsAttribute: String

var kAXLinkedUIElementsAttribute: String

var kAXRowsAttribute: String

An array of the accessibility objects representing the rows in this table or outline view.

var kAXVisibleRowsAttribute: String

An array of the accessibility objects representing the currently visible rows in this table or outline view.

var kAXSelectedRowsAttribute: String

An array of the accessibility objects representing the currently selected rows in this table or outline view.

var kAXColumnsAttribute: String

An array of the accessibility objects representing the columns in this browser view.

var kAXVisibleColumnsAttribute: String

An array of the accessibility objects representing the currently visible columns in this browser view.

var kAXSelectedColumnsAttribute: String

An array of the accessibility objects representing the currently selected columns in this browser view.

var kAXSortDirectionAttribute: String

The sort direction of this accessibility object’s contents. For example, a list view’s contents may be sorted in ascending or descending order.

var kAXColumnHeaderUIElementsAttribute: String

An array of accessibility objects representing the column headers of this table or browser view.

var kAXIndexAttribute: String

The index of the row or column represented by this accessibility object.

var kAXDisclosingAttribute: String

Indicates whether a row in an outline view represented by this accessibility object has an open or closed disclosure triangle. `true` indicates an open disclosure triangle; `false` indicates a closed disclosure triangle.

var kAXDisclosedRowsAttribute: String

An array of accessibility objects representing the disclosed rows of this user interface element.

var kAXDisclosedByRowAttribute: String

The accessibility object representing the disclosing row.

var kAXMatteHoleAttribute: String

The accessibility object that represents the area available to the user through the matte hole.

var kAXMatteContentUIElementAttribute: String

The accessibility object clipped by the matte.

var kAXIsApplicationRunningAttribute: String

Indicates if the application represented by the Dock icon this accessibility object represents is currently running.

var kAXFocusedApplicationAttribute: String

var kAXInsertionPointLineNumberAttribute: String

The line number of the insertion point in the text associated with this accessibility object.

## See Also

### Accessibility Object Constants

Roles

Define the values an accessibility object’s role attribute can have.

Subroles

Define the values for an accessibility object’s subrole attribute.

Parameterized Attributes

Define the parameterized attributes an accessibility object can have.

Actions

Define the actions an accessibility object can perform.

Notifications

Define the notifications that can be broadcast by an accessibility object.

Orientations and Sort Directions

Define the values for the orientation and sort-direction attributes of some accessibility objects.

