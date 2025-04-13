

- macOS Release Notes
- macOS Big Sur 11.0.1 Release Notes
-  AppKit Release Notes for macOS Big Sur 11 

Article

# AppKit Release Notes for macOS Big Sur 11

Update your apps to use new features, and test your apps against API changes.

## Overview

AppKit in macOS 11 includes new features, as well as API changes and deprecations.

### New Features

#### NSAlert

- Apps linked on or after macOS 11 beta automatically get a new, more vertically oriented alert layout and appearance as part of the new system look. AppKit’s NSAlert API remains the same as on macOS Catalina 10.15, and most apps won’t need to make any changes to their uses of it, but it’s a good practice to check that all of your app’s alerts present their content properly, because the new layout may break some existing assumptions. There is also a new hasDestructiveAction property on NSButton that you use to flag alert buttons whose actions have a dangerous effect on user data.

- The main overall change is a vertically stacked, mostly single-column layout that typically produces narrower alert panels or sheets than in previous OS releases. This change in alert width affects line wrap of messageText and informativeText content. Apps that use hard line breaks in their alert text or count on line wrap occurring at particular places in previous releases may need to reformat their alert content for macOS Big Sur 11 beta. Uses of accessoryView with NSAlerts may likewise need revising to work well with `NSAlert`s’ new layout and appearance. Controls presented in an alert’s `accessoryView` should use the new .large control size on macOS Big Sur 11 beta. You may also reconsider the width of each `accessoryView` you’re using. An alert will widen itself when feasible to accommodate a given `accessoryView`‘s width (in previous releases, an `NSAlert` attempts to maintain the frame size of the `accessoryView`), but the resultant alert’s proportions might not fit optimally with the system look, if the `accessoryView` is very wide. In such cases, you may want to reduce the accessoryView’s width if that can be done without negatively impacting user interaction with the `accessoryView`’s controls.

- In most cases, an alert that contains buttons now has those buttons vertically stacked at the bottom of the alert. An alert that contains exactly two buttons may present those buttons side-by-side if there is sufficient horizontal space to accommodate them. An alert that contains four or more buttons may display those buttons with an alternative appearance that features rollover bezels and separator lines. Buttons are generally presented in the order in which they are added, but you may move a Cancel button (identified by having a `keyEquivalent` of Escape) to the bottom and offset it from the other buttons.

- Alert panels or sheets are constrained to a system-determined maximum height. You may place content that exceeds that height in scroll views. This content currently includes the alert’s `messageText` and `informativeText`, but may encompass other content as well. In general, use alerts for short interactions where there is a small amount of information to present to the user, and a small, simple set of actions from which they choose. When you have more substantial content to present, consider presenting a generalized panel or sheet of your own design using the NSWindow or NSPanel APIs.

- If any of your alerts contain buttons, which trigger an action that could have a destructive effect on user data (for example, causing unsaved changes to be irretrievably discarded), marking those buttons with `hasDestructiveAction = true` is recommended. Doing so may give those buttons a special, cautionary appearance in certain contexts (currently, `NSAlert`s and Open/Save Panels), as well as some basic safeguards against inadvertent presses. See NSButton for details.

#### NSAppearance

- current is now marked for deprecation. A new read-only class property, `currentDrawingAppearance`, replaces it. A new instance method, `performAsCurrentDrawingAppearance:` will set the receiver as the `currentDrawingAppearance` and perform a block, then restore the previous state of `currentDrawingAppearance`.

#### NSApplication

- If the Info.plist file for the app does not contain the NSPrincipalClass key, AppKit will default to using NSApplication as the principal class when NSApplicationMain(_:_:) is called.

- The keys `NSSupportsAutomaticTermination` and `NSSupportsSuddenTermination` are no longer part of the default Info.plist for new Xcode projects. This ensures that applicationWillTerminate(_:) is called during termination, in cases where disableSuddenTermination or enableSuddenTermination is not used to explicitly manage the ability to quickly exit the app.

#### NSBeep

- doc://com.apple.documentation/documentation/appkit/1473622-nsbeep will omit playing a sound if a prior `NSBeep` is currently playing one.

#### NSBrowser

- NSBrowser instances inherit a new appearance in apps linked on or after macOS Big Sur 11 beta, inheriting the new `.inset` style of NSTableView with its updated metrics (including increased row height) and rounded-rect selection highlight style. Apps are encouraged to use NSBrowserCell, as its implementation contains needed cell padding, image-text spacing, and text-baseline adjustments for the new style. Those using custom-cell classes may need to make adjustments to match the new metrics. NSMatrix-based NSBrowsers, which were deprecated in macOS 10.10, maintain their existing metrics and appearance.

#### NSButton

- NSButton and its subclasses now draw more content outside their alignment rects. Therefore, if you pin them to a superview without any margins, the control will appear clipped. To resolve this issue, ensure that your controls are pinned with a minimum of standard space to the parent, rather than zero, to allow for sufficient space to fully draw the artwork. Alternatively, place your controls in NSStackView or NSGridView, which won’t clip their contents to the frame. `NSStackView` has had this behavior since inception; NSGridView adopts this behavior as of macOS Big Sur 11 beta 4.

- Sometimes, the action to which a button is wired to will have a dangerous or destructive effect on user data (such as causing unsaved changes to be irretrievably discarded). NSButton has a new hasDestructiveAction property in macOS Big Sur 11 beta that defaults to `false`, but can be set to `true` to identify such buttons. This practice is encouraged, because it enables AppKit to distinguish such buttons with a cautionary visual appearance (currently, a red-color label in `NSAlert`s and Open/Save Panels for buttons that don’t have an accent color applied), and apply event-handling safeguards that help protect the buttons against accidental presses. The system copies and archives the new `hasDestructiveAction` property with a given button instance.

#### NSCell Mouse Tracking

- The `lastPoint` sent to doc://com.apple.documentation/documentation/appkit/nscell/1535599-continuetracking was always the mouseDown(with:) point instead of the point or the previous event. This caused problems with NSCell subclasses and has been resolved for apps linked on or after macOS Big Sur 11 beta.

#### NSImage

- If your application uses the `NSListView` or `NSTextListSmall` named images, they will automatically flip if your application is running in a right-to-left language such as Arabic or Hebrew. You can’t opt out of this new behavior, so if you were previously manually flipping these images programmatically, you no longer need to do this.

#### NSMenu

- NSMenu now implements the NSAppearanceCustomization protocol. However, the specified appearance is only observed for popup menus. Menus that are in the main menu bar always use the system-wide appearance, regardless of what appearance has been set on the menu. For a popup menu, the effectiveAppearance method returns the appearance of the menu itself or any of its supermenus; if no appearance has been explicitly specified, the menu’s effective appearance is the appearance of the presenting view or window, or the app itself.

- Note that the symbols images returned from the onStateImage, offStateImage, and mixedStateImage methods on NSMenu are not configured images, and should be configured appropriately by the caller. The standard configuration for a menu item state image is NSImage.SymbolScale.small scale and bold weight.

### NSOpenSavePanelDelegate

- As of macOS Catalina 10.15, you cannot use panel(_:userEnteredFilename:confirmed:) to modify a filename if an app is running in a sandbox. In macOS Big Sur 11, non-sandboxed apps can change the filename’s extension. Sandboxed apps remain unable to change a filename.

### NSOutlineView

- Other than source lists, the height of group rows in NSOutlineView now follows the same rules as NSTableView. Group rows get the default height (28pt in macOS Big Sur 11) unless doc://com.apple.documentation/documentation/appkit/nsoutlineviewdelegate/1531870-outlineview is implemented in the delegate. This matches more closely the group row height behavior for source lists. Apps linked against macOS Catalina or an earlier SDK continue to use the legacy behavior.

#### NSPrintOperation

- You must initialize the frame of NSPrintOperation’s printing view either before or during doc://com.apple.documentation/documentation/appkit/nsview/1483774-knowspagerange. Doing this later (for example, during rectForPage(_:) or adjustPageHeightNew(_:top:bottom:limit:)) causes problems, and AppKit now logs an error and stops in the debugger if it encounters this behavior.

#### NSScrollView

- When linked on macOS Big Sur 11 or later, an NSScrollView with automaticallyAdjustsContentInsets set to `true` will continue to respect the safe-area insets of the window even when titlebarAppearsTransparent is set to `true`. For apps linked earlier than macOS Big Sur 11 `NSScrollView` will ignore the automatic insets when `titlebarAppearsTransparent` is set to `true`.

#### NSSearchField

- In macOS Mojave 10.14, NSSearchField stopped supporting the centered placeholder string configuration. The value in the `centersPlaceholder` property is always ignored, and the placeholder and contents are always aligned according to the alignment property value. In macOS Big Sur 11 beta, centersPlaceholder along with the 3 overridable methods for customizing the search field element geometry, depending on the centering state, are soft-deprecated.

- New overridable methods to customize the geometry of 3 search field elements (text, search button, and cancel button) are now available. searchTextBounds is replacing rectForSearchText(whenCentered:). There are searchButtonRect(forBounds:) for rectForSearchButton(whenCentered:) and cancelButtonBounds for rectForCancelButton(whenCentered:).

#### NSSearchToolbarItem

- A new NSToolbarItem subclass, NSSearchToolbarItem, is introduced in macOS Big Sur 11 beta. The toolbar item provides the standard behavior for showing an `NSSearchField` in the toolbar.

- `NSSearchToolbarItem` has a property that controls the first responder/keyboard focus state of the field with the cancel button action, resignsFirstResponderWithCancel. Handle the first responder behavior based on the way macOS presents search results.

  The first type is the filtering search. The results are presented by filtering non-matching items from a list. Apps like Mail and Notes are in this group. The search field resigns the first responder/key focus state with the cancel button click, in addition to clearing the search string.

  The second type is the query search. macOS presents the results by showing a designated view. Finder and Calendar are of this type. The search remains focused, with the cancel button allowing continued search sessions.

  The query type search apps changes `resignsFirstResponderWithCancel` to `false`.

#### NSSegmentedControl

- Prior to macOS Big Sur 11 beta 9, segments with NSImageScaling.scaleProportionallyUpOrDown image scaling did not correctly scale upward to fill the segment’s content bounds. macOS now applies upscaling correctly for apps linked on the 11 beta SDK and newer versions. Apps built on prior SDKs will continue to receive the old scaling behavior for compatibility.

#### NSSlider

- The `frame` of NSSlider has changed in macOS Big Sur 11.

- To ensure horizontal sliders appropriately align vertically with surrounding or nearby UI elements (like a `label`), use Auto Layout with the slider’s baseline.

- If your app cannot or does not use Auto Layout, you may query the lastBaselineOffsetFromBottom property to manually offset the view.

- Some `NSSlider`s you create using Interface Builder with Xcode 11 or earlier and that you open using Interface Builder with Xcode 12 won’t automatically have adjusted frames that match new control metrics in macOS Big Sur 11. These `NSSlider`s may also appear visually clipped. To manually adjust the slider’s frame to match the new control metrics, either add Auto Layout constraints to the frame, or select the frame and and choose Editor \> Size to Fit Content.

#### NSStatusItem

- NSStatusItem no longer follows the app appearance for its view. Status items using custom views use the effectiveAppearance API to determine which appearance to draw.

#### NSTableCellView

- Labels in group rows will have their appearance set by NSTableCellView for all table view styles and not only source lists. macOS Big Sur 11 defines the appearance of regular table views and will also set the default look on the group row cell view NSTextField. Due to the significant nature of this change, it is only enabled for apps linked against the macOS Big Sur 11 SDK.

  To opt-out of this behavior, avoid setting the `textField` property on the `NSTableCellView` instance, whether in Interface Builder, or in a subclass in code. If you choose to opt-out, the app must fully manage the group-row label appearance.

#### NSTitlebarAccessoryViewController

- Apps linked on or after macOS 11 with controllers configured with a layoutAttribute of `NSLayoutAttributeBottom` will automatically adjust their size to the system default standard sizing (for example, `automaticallyAdjustsSize` is set to `true`).

#### Sheets

- Prior to macOS Big Sur 11 beta 9, the animation to show and dismiss a sheet was run in a private runloop mode, which prevented other runloop sources, such as timers, from executing during the animation. Beginning in macOS Big Sur 11, the sheet animation runs in a common runloop mode to more quickly make the sheet the key window, among other benefits. Due to binary compatibility concerns, this change is enabled only for apps linked on macOS Big Sur.

#### Symbols

- Symbols with directional names such as “left” and “right” no longer flip in right-to-left languages. If your app depends on the flipping behavior, adopt the new symbols that do flip automatically, such as “chevron.forward” instead of “chevron.right”.

