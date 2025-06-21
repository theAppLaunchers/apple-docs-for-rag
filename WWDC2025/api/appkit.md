Framework

# AppKit

Construct and manage a graphical, event-driven user interface for your macOS app.

Mac Catalyst 13.0+macOS 10.0+

## [Overview](/documentation/AppKit#overview)

AppKit contains the objects you need to build the user interface for a macOS app. In addition to drawing windows, buttons, panels, and text fields, it handles all the event management and interaction between your app, people, and macOS.

![An image of the Landmarks sample app on Mac showing the Mount Fuji landmark.](https://docs-assets.developer.apple.com/published/2ba3100f3acde10ba4fbbbdb32b4cbda/landmarks-app-article-hero%402x.png)

Aside from drawing and managing interactions, AppKit handles printing, animating, as well as creating documents with large amounts of data efficiently. The framework also contains built-in support for localization and accessibility to ensure that your app reaches as many people as possible.

AppKit also works with [SwiftUI](/documentation/SwiftUI), so you can implement parts of your AppKit app in SwiftUI or mix interface elements between the two frameworks. For example, you can place AppKit views and view controllers inside SwiftUI views, and vice versa.

Note

For information about bringing your iPad app to Mac, see [Mac Catalyst](/documentation/UIKit/mac-catalyst). To build an iOS app, you can use SwiftUI to create an app that works across all of Apple’s platforms, or use [UIKit](/documentation/UIKit) to create an app for iOS only.

## [Topics](/documentation/AppKit#topics)

### [Essentials](/documentation/AppKit#Essentials)

[

Adopting Liquid Glass](/documentation/TechnologyOverviews/adopting-liquid-glass)

Find out how to bring the new material to your app.

[

AppKit updates](/documentation/Updates/AppKit)

Learn about important changes to AppKit.

[

Protecting the User’s Privacy](/documentation/UIKit/protecting-the-user-s-privacy)

Secure personal data, and respect user preferences for how data is used.

[

Porting your macOS apps to Apple silicon](/documentation/Apple-Silicon/porting-your-macos-apps-to-apple-silicon)

Create a version of your macOS app that runs on both Apple silicon and Intel-based Mac computers.

### [App Structure](/documentation/AppKit#App-Structure)

[

API Reference

App and Environment](/documentation/appkit/app-and-environment)

Learn about the objects that you use to interact with the system.

[

API Reference

Documents, Data, and Pasteboard](/documentation/appkit/documents-data-and-pasteboard)

Organize your app’s data and preferences, and share that data on the pasteboard or in iCloud.

[

API Reference

Cocoa Bindings](/documentation/appkit/cocoa-bindings)

Automatically synchronize your data model with your app’s interface using Cocoa Bindings.

[

API Reference

Resource Management](/documentation/appkit/resource-management)

Manage the storyboards and nib files containing your app’s user interface, and learn how to load data that is stored in resource files.

[

API Reference

App Extensions](/documentation/appkit/app-extensions)

Extend your app’s basic functionality to other parts of the system.

### [User Interface](/documentation/AppKit#User-Interface)

Your app’s user interface provides visual, audible, and tactile feedback to the user about what your app is doing.

[

API Reference

Views and Controls](/documentation/appkit/views-and-controls)

Present your content onscreen and handle user input and events.

[

API Reference

View Management](/documentation/appkit/view-management)

Manage your user interface, including the size and position of views in a window.

[

API Reference

View Layout](/documentation/appkit/view-layout)

Position and size views using a stack view or Auto Layout constraints.

[

API Reference

Appearance Customization](/documentation/appkit/appearance-customization)

Add Dark Mode support to your app, and use appearance proxies to modify your UI.

[

API Reference

Animation](/documentation/appkit/animation)

Animate your views and other content to create a more engaging experience for users.

[

API Reference

Windows, Panels, and Screens](/documentation/appkit/windows-panels-and-screens)

Organize your view hierarchies and facilitate their display onscreen.

[

API Reference

Sound, Speech, and Haptics](/documentation/appkit/sound-speech-and-haptics)

Play sounds and haptic feedback, and incorporate speech recognition and synthesis into your interface.

[

Supporting Continuity Camera in Your Mac App](/documentation/appkit/supporting-continuity-camera-in-your-mac-app)

Incorporate scanned documents and pictures from a user’s iPhone, iPad, or iPod touch into your Mac app using Continuity Camera.

### [User Interactions](/documentation/AppKit#User-Interactions)

[

API Reference

Mouse, Keyboard, and Trackpad](/documentation/appkit/mouse-keyboard-and-trackpad)

Handle events related to mouse, keyboard, and trackpad input.

[

API Reference

Menus, Cursors, and the Dock](/documentation/appkit/menus-cursors-and-the-dock)

Implement menus and cursors to facilitate interactions with your app, and use your app’s Dock tile to convey updated information.

[

API Reference

Gestures](/documentation/appkit/gestures)

Encapsulate your app’s event-handling logic in gesture recognizers so that you can reuse that code throughout your app.

[

API Reference

Touch Bar](/documentation/appkit/touch-bar)

Display interactive content and controls in the Touch Bar.

[

API Reference

Drag and Drop](/documentation/appkit/drag-and-drop)

Support the direct manipulation of your app’s content using drag and drop.

[

API Reference

Accessibility for AppKit](/documentation/appkit/accessibility-for-appkit)

Make your AppKit apps accessible to everyone who uses macOS.

### [Graphics, Drawing, Color, and Printing](/documentation/AppKit#Graphics-Drawing-Color-and-Printing)

[

API Reference

Images and PDF](/documentation/appkit/images-and-pdf)

Create and manage images, in bitmap, PDF, and other formats.

[

API Reference

Drawing](/documentation/appkit/drawing)

Draw shapes, images, and other content on the screen.

[

API Reference

Color](/documentation/appkit/color)

Represent colors using built-in or custom formats, and give users options for selecting and applying colors.

[

API Reference

Printing](/documentation/appkit/printing)

Display the system print panels and manage the printing process.

### [Text](/documentation/AppKit#Text)

[

API Reference

Text Display](/documentation/appkit/text-display)

Display text and check spelling.

[

API Reference

TextKit](/documentation/appkit/textkit)

Manage text storage and perform custom layout of text-based content in your app’s views.

[

API Reference

Fonts](/documentation/appkit/fonts)

Manage the fonts used to display text.

[

API Reference

Writing Tools](/documentation/appkit/writing-tools)

Add support for Writing Tools to your app’s text views.

### [Deprecated](/documentation/AppKit#Deprecated)

Avoid using deprecated classes and protocols in your apps.

[

API Reference

Deprecated Symbols](/documentation/appkit/deprecated-symbols)

Review symbols that are no longer supported, and find the replacements to use instead.

### [Reference](/documentation/AppKit#Reference)

[

API Reference

Enumerations](/documentation/appkit/enumerations)

Enumerations for use with multiple classes.

[

API Reference

Constants](/documentation/appkit/constants)

Constants for use with multiple classes.

[

API Reference

Data Types](/documentation/appkit/data-types)

Data types for use with multiple classes.

[

API Reference

Macros](/documentation/appkit/macros)

Macros for use with multiple classes.