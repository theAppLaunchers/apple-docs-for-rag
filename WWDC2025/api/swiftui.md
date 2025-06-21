Framework

# SwiftUI

Declare the user interface and behavior for your app on every platform.

iOS 13.0+iPadOS 13.0+Mac Catalyst 13.0+macOS 10.15+tvOS 13.0+visionOS 1.0+watchOS 6.0+

## [Overview](/documentation/SwiftUI#Overview)

SwiftUI provides views, controls, and layout structures for declaring your app’s user interface. The framework provides event handlers for delivering taps, gestures, and other types of input to your app, and tools to manage the flow of data from your app’s models down to the views and controls that users see and interact with.

Define your app structure using the [`App`](/documentation/swiftui/app) protocol, and populate it with scenes that contain the views that make up your app’s user interface. Create your own custom views that conform to the [`View`](/documentation/swiftui/view) protocol, and compose them with SwiftUI views for displaying text, images, and custom shapes using stacks, lists, and more. Apply powerful modifiers to built-in views and your own views to customize their rendering and interactivity. Share code between apps on multiple platforms with views and controls that adapt to their context and presentation.

![An image of the Landmarks sample app on Mac, iPad, and iPhone showing the Mount Fuji landmark.](https://docs-assets.developer.apple.com/published/ce193ec494e91d4150c3356442824213/landmarks-app-article-hero%402x.png)

You can integrate SwiftUI views with objects from the [UIKit](/documentation/UIKit), [AppKit](/documentation/AppKit), and [WatchKit](/documentation/WatchKit) frameworks to take further advantage of platform-specific functionality. You can also customize accessibility support in SwiftUI, and localize your app’s interface for different languages, countries, or cultural regions.

### [Featured samples](/documentation/SwiftUI#Featured-samples)

[

![An image with a background of Mount Fuji, and in the foreground screenshots of the landmark detail view for Mount Fuji in the Landmarks app, in an iPad and iPhone.](https://docs-assets.developer.apple.com/published/54d1e5049c272381ddeb6c5d7b04fd25/Landmarks-Building-an-app-with-Liquid-Glass-PageImage-card%402x.png)

Landmarks: Building an app with Liquid Glass

Enhance your app experience with system-provided and custom Liquid Glass.

View sample code

](/documentation/swiftui/landmarks-building-an-app-with-liquid-glass)

[

![](https://docs-assets.developer.apple.com/published/648c665254129674ce04bbc64dbeeb2d/Destination-Video-intro%402x.png)

Destination Video

Leverage SwiftUI to build an immersive media experience in a multiplatform app.

View sample code

](/documentation/visionOS/destination-video)

[

![](https://docs-assets.developer.apple.com/published/d9f7d85cd82f76e6fd53df7302f0424a/BOT-anist-PageImage-card%402x.png)

BOT-anist

Build a multiplatform app that uses windows, volumes, and animations to create a robot botanist’s greenhouse.

View sample code

](/documentation/visionOS/BOT-anist)

[

![A screenshot displaying the document launch experience on iPad with a robot and plant accessory to the left and right of the title view, respectively.](https://docs-assets.developer.apple.com/published/e143ff39a1e48efe1ed0000f6e902a5b/Building-a-document-based-app-PageImage-card%402x.png)

Building a document-based app with SwiftUI

Create, save, and open documents in a multiplatform app.

View sample code

](/documentation/swiftui/building-a-document-based-app-with-swiftui)

## [Topics](/documentation/SwiftUI#topics)

### [Essentials](/documentation/SwiftUI#Essentials)

[

Adopting Liquid Glass](/documentation/TechnologyOverviews/adopting-liquid-glass)

Find out how to bring the new material to your app.

[

Learning SwiftUI](/tutorials/swiftui-concepts)

Discover tips and techniques for building multiplatform apps with this set of conceptual articles and sample code.

[

Exploring SwiftUI Sample Apps](/tutorials/Sample-Apps)

Explore these SwiftUI samples using Swift Playgrounds on iPad or in Xcode to learn about defining user interfaces, responding to user interactions, and managing data flow.

[

SwiftUI updates](/documentation/Updates/SwiftUI)

Learn about important changes to SwiftUI.

[

Landmarks: Building an app with Liquid Glass](/documentation/swiftui/landmarks-building-an-app-with-liquid-glass)

Enhance your app experience with system-provided and custom Liquid Glass.

### [App structure](/documentation/SwiftUI#App-structure)

[

API Reference

App organization](/documentation/swiftui/app-organization)

Define the entry point and top-level structure of your app.

[

API Reference

Scenes](/documentation/swiftui/scenes)

Declare the user interface groupings that make up the parts of your app.

[

API Reference

Windows](/documentation/swiftui/windows)

Display user interface content in a window or a collection of windows.

[

API Reference

Immersive spaces](/documentation/swiftui/immersive-spaces)

Display unbounded content in a person’s surroundings.

[

API Reference

Documents](/documentation/swiftui/documents)

Enable people to open and manage documents.

[

API Reference

Navigation](/documentation/swiftui/navigation)

Enable people to move between different parts of your app’s view hierarchy within a scene.

[

API Reference

Modal presentations](/documentation/swiftui/modal-presentations)

Present content in a separate view that offers focused interaction.

[

API Reference

Toolbars](/documentation/swiftui/toolbars)

Provide immediate access to frequently used commands and controls.

[

API Reference

Search](/documentation/swiftui/search)

Enable people to search for text or other content within your app.

[

API Reference

App extensions](/documentation/swiftui/app-extensions)

Extend your app’s basic functionality to other parts of the system, like by adding a Widget.

### [Data and storage](/documentation/SwiftUI#Data-and-storage)

[

API Reference

Model data](/documentation/swiftui/model-data)

Manage the data that your app uses to drive its interface.

[

API Reference

Environment values](/documentation/swiftui/environment-values)

Share data throughout a view hierarchy using the environment.

[

API Reference

Preferences](/documentation/swiftui/preferences)

Indicate configuration preferences from views to their container views.

[

API Reference

Persistent storage](/documentation/swiftui/persistent-storage)

Store data for use across sessions of your app.

### [Views](/documentation/SwiftUI#Views)

[

API Reference

View fundamentals](/documentation/swiftui/view-fundamentals)

Define the visual elements of your app using a hierarchy of views.

[

API Reference

View configuration](/documentation/swiftui/view-configuration)

Adjust the characteristics of views in a hierarchy.

[

API Reference

View styles](/documentation/swiftui/view-styles)

Apply built-in and custom appearances and behaviors to different types of views.

[

API Reference

Animations](/documentation/swiftui/animations)

Create smooth visual updates in response to state changes.

[

API Reference

Text input and output](/documentation/swiftui/text-input-and-output)

Display formatted text and get text input from the user.

[

API Reference

Images](/documentation/swiftui/images)

Add images and symbols to your app’s user interface.

[

API Reference

Controls and indicators](/documentation/swiftui/controls-and-indicators)

Display values and get user selections.

[

API Reference

Menus and commands](/documentation/swiftui/menus-and-commands)

Provide space-efficient, context-dependent access to commands and controls.

[

API Reference

Shapes](/documentation/swiftui/shapes)

Trace and fill built-in and custom shapes with a color, gradient, or other pattern.

[

API Reference

Drawing and graphics](/documentation/swiftui/drawing-and-graphics)

Enhance your views with graphical effects and customized drawings.

### [View layout](/documentation/SwiftUI#View-layout)

[

API Reference

Layout fundamentals](/documentation/swiftui/layout-fundamentals)

Arrange views inside built-in layout containers like stacks and grids.

[

API Reference

Layout adjustments](/documentation/swiftui/layout-adjustments)

Make fine adjustments to alignment, spacing, padding, and other layout parameters.

[

API Reference

Custom layout](/documentation/swiftui/custom-layout)

Place views in custom arrangements and create animated transitions between layout types.

[

API Reference

Lists](/documentation/swiftui/lists)

Display a structured, scrollable column of information.

[

API Reference

Tables](/documentation/swiftui/tables)

Display selectable, sortable data arranged in rows and columns.

[

API Reference

View groupings](/documentation/swiftui/view-groupings)

Present views in different kinds of purpose-driven containers, like forms or control groups.

[

API Reference

Scroll views](/documentation/swiftui/scroll-views)

Enable people to scroll to content that doesn’t fit in the current display.

### [Event handling](/documentation/SwiftUI#Event-handling)

[

API Reference

Gestures](/documentation/swiftui/gestures)

Define interactions from taps, clicks, and swipes to fine-grained gestures.

[

API Reference

Input events](/documentation/swiftui/input-events)

Respond to input from a hardware device, like a keyboard or a Touch Bar.

[

API Reference

Clipboard](/documentation/swiftui/clipboard)

Enable people to move or duplicate items by issuing Copy and Paste commands.

[

API Reference

Drag and drop](/documentation/swiftui/drag-and-drop)

Enable people to move or duplicate items by dragging them from one location to another.

[

API Reference

Focus](/documentation/swiftui/focus)

Identify and control which visible object responds to user interaction.

[

API Reference

System events](/documentation/swiftui/system-events)

React to system events, like opening a URL.

### [Accessibility](/documentation/SwiftUI#Accessibility)

[

API Reference

Accessibility fundamentals](/documentation/swiftui/accessibility-fundamentals)

Make your SwiftUI apps accessible to everyone, including people with disabilities.

[

API Reference

Accessible appearance](/documentation/swiftui/accessible-appearance)

Enhance the legibility of content in your app’s interface.

[

API Reference

Accessible controls](/documentation/swiftui/accessible-controls)

Improve access to actions that your app can undertake.

[

API Reference

Accessible descriptions](/documentation/swiftui/accessible-descriptions)

Describe interface elements to help people understand what they represent.

[

API Reference

Accessible navigation](/documentation/swiftui/accessible-navigation)

Enable users to navigate to specific user interface elements using rotors.

### [Framework integration](/documentation/SwiftUI#Framework-integration)

[

API Reference

AppKit integration](/documentation/swiftui/appkit-integration)

Add AppKit views to your SwiftUI app, or use SwiftUI views in your AppKit app.

[

API Reference

UIKit integration](/documentation/swiftui/uikit-integration)

Add UIKit views to your SwiftUI app, or use SwiftUI views in your UIKit app.

[

API Reference

WatchKit integration](/documentation/swiftui/watchkit-integration)

Add WatchKit views to your SwiftUI app, or use SwiftUI views in your WatchKit app.

[

API Reference

Technology-specific views](/documentation/swiftui/technology-specific-views)

Use SwiftUI views that other Apple frameworks provide.

### [Tool support](/documentation/SwiftUI#Tool-support)

[

API Reference

Previews in Xcode](/documentation/swiftui/previews-in-xcode)

Generate dynamic, interactive previews of your custom views.

[

API Reference

Xcode library customization](/documentation/swiftui/xcode-library-customization)

Expose custom views and modifiers in the Xcode library.

[

API Reference

Performance analysis](/documentation/swiftui/performance-analysis)

Measure and improve your app’s responsiveness.