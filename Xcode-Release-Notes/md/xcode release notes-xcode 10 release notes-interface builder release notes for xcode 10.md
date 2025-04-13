

- Xcode Release Notes
- Xcode 10 Release Notes
-  Interface Builder Release Notes for Xcode 10 

Article

# Interface Builder Release Notes for Xcode 10

Update your apps to use new features, and test your apps against changes.

## Overview

Read these notes when you’re building interfaces in Xcode 10.

### New Features

- Resizing a UIStackView or NSStackView along its distribution axis in the canvas will adjust spacing between items. (21166308)

- Control-dragging from Interface Builder to a Swift source file defaults to creating `@IBOutlet` when the insertion point is above the first method in a class, and `@IBAction` otherwise. (36891045)

- Notification categories now have a “Handles Grouping” property, which allows notifications to be coalesced.

- Static notification interfaces now support connecting a subtitle label outlet.

- The “Stack” button in the canvas bar has been replaced with a pop-up menu containing all embedding options for the selection. (38201831)

- The default colors for NSTextField and NSTextView have been changed. The new values are still appropriate for deployment on macOS 10.13 and earlier.

- The menu for choosing a font family in the Attributes inspector now renders a preview of each font. (37157540)

- The NSVisualEffectView class’s inherited appearance inspector property has a backwards deployment option of Vibrant Light or Vibrant Dark for previous versions of macOS. (40536518)

- NSVisualEffectView will backwards deploy new standard semantic 10.14 materials to appropriate materials for prior OSes. (40511407)

- On macOS 10.14, NSToolbarItem can center itself in an NSToolbar by checking “Is Centered Item” in the Attributes inspector.

- An NSToolbarItem containing an image or custom view has an Automatic size option in the Size inspector. Use this option to automatically manage the minimum and maximum width and height of the toolbar item, for example when the item contains a segmented control.

- Support for Large Title font text style (largeTitle) on iOS 11 and later, and on watchOS 5. (33150633)

- In the Identity inspector, the localization comment field has been changed to plain text. It is still stored in the document as an attributed string to maintain compatibility with earlier versions of Xcode. (39856810)

- The exception “Impossible to set up layout with view hierarchy unprepared for constraint.” has improved diagnostics. (42514606)

- New UILabel inspector property “Marquee on Ancestor Focus” for controlling scrolling behavior.

- On macOS 10.14, NSButton and NSImage support content color tinting in the Attributes inspector. Tinting only applies to borderless buttons and template images.

- The Editor \> Embed In menu item allows embedding in a tightly wrapped view that doesn’t add any margins to the selected content. (11515741)

- Inspector color pickers now use a standard pop-up button. The color swatch can be dragged by holding the Option key. (38582636)

- Designable NSView subclasses are rendered with the appropriate NSAppearance for their use in the canvas.

- The macOS library now contains an “Import From Device” menu item for Continuity Camera. Its submenu will be auto-populated at runtime on macOS 10.14 and higher; on previous versions, it will be disabled and have no submenu. (41474755)

- The new Volume control for watchOS 5 now allows setting tint color. (40830006)

- Opening a `.nib` or `.xib` file last saved in a format prior to Xcode 5 now prompts for confirmation, and automatically upgrades the document to a modern format. (37691996)

- Support for the new Dynamic Interactive notification interfaces.

- Scrolling performance, especially in very large storyboards, is improved. (34904204)

- When a Mac XIB or storyboard is opened in Xcode 10, NSTextView that have default colors will be changed to use new recommended colors. The text color and insertion point color change from black to textColor, and the background color changes from white to textBackgroundColor. These should appear the same on earlier releases while also adapting to appearances on macOS 10.14. Editable NSTextField instances have their text color changed from textColor to controlTextColor. These changes only apply when opening and saving the document from within Xcode.

- Discouraged uses of Vibrant Light and Vibrant Dark appearance are now reported. NSPopover and NSVisualEffectView are exempted. (42036478)

- Support for the new “Now Playing” and “Volume” interface objects.

- Controls using named colors from an asset catalog now update as the value of the color changes. (37613468)

- Image and color inspector properties that reference an asset catalog resource have a navigation button to jump to that resource. Option + click will show the resource in the Assistant Editor. (39661055)

- Support for new NSVisualEffectView materials introduced in macOS 10.14.

- Some binaries used by Interface Builder have been renamed for better consistency. Instead of “Interface Builder Cocoa Touch Tool”, “Interface Builder WatchKit Tool”, and “IBAppleTVTool”, they are now called “IBAgent-*\[platform\]*”. (35400833)

- On macOS 10.14, the Device Bar and Preview assistant editor allow designing for and previewing in Light Appearance and Dark Appearance.

- Support for NSGridView, which manages Auto Layout constraints for its content in a two-dimensional table layout. NSGridView is backward deployable to macOS 10.12, or macOS 10.13.4 when using merged cells.

- Canvas rendering now happens in parallel, and scales based on demand and hardware to improve the performance of edit operations, particularly for large scenes. (36999759)

- Support for setting accessibility attributes on NSWindow.

- NSTextView has multiple entries in the object library. This separates configurations appropriate for user interface elements that should adapt to the system appearance, and document content which has a fixed appearance that does not change with the system setting, including for print content.

### Known Issues

- Displaying `NSOpenGLView` instances in Interface Builder when running on macOS 10.13 may result in a crash. (43849153)

### Resolved Issues

- Fixed an issue with rendering table view cells that are scrolled out of view at design time. (41213048)

- Fixed a problem where issues for different objects were incorrectly coalesced. (13162286)

- Fixed an issue where clicking a build issue wouldn’t select the referenced object in the canvas. (14779509)

- Fixed a crash when viewing the Attributes inspector for an NSLevelIndicatorCell in a cell-based NSTableView. (39231884)

- Fixed an issue where storyboard view controllers would change their relative placement unexpectedly while navigating between code and the Interface Builder canvas. (40925441)

- Fixed an issue that would cause the view hierarchy to not render if the canvas area was scrolled before presenting the view hierarchy. (27635197)

- Fixed an issue where connect-to-source mistakenly allowed adding code to Swift generated interfaces. (35263074)

- When adding constraints with the control-drag canvas menu, shift-clicking on multiple items no longer requires clicking an “Add Constraints” menu item, simply clicking outside the menu now works. (22970158)

- Improved performance compiling documents, particularly those containing multiple NSComboBox controls. (30468986)

- `@IBDesignable` views now build using the new build system when it is enabled. (31433718)

- Typing delete (⌫) when an edge is selected in the constraint filter of the Size inspector now removes the applicable constraints, rather than the view itself. (25373426)

- Custom fonts are supported in watchOS dynamic notifications. (35843402)

- Fixed an issue where `@IBDesignable` views would not build when the project includes a WatchKit target. (36281806)

- Fixed a problem with scenes drawing blank when table view cells are scrolled beyond the UITableView bounds. (39338152)

- When adding constraints with the control-drag canvas menu, shift-clicking on multiple items now adds them to the canvas instantly, rather than after the menu is closed. (18991966)

- Embedding views in macOS documents now supports NSVisualEffectView. (39924232)

## See Also

### Release Notes

Build System Release Notes for Xcode 10

Update your apps to use new features, and test your apps against changes.

Source Editor Release Notes for Xcode 10

Update your programming workflow to use new features, and test your workflow against changes.

Swift 4.2 Release Notes for Xcode 10

Update your code to use new language features and test your apps against changes.

