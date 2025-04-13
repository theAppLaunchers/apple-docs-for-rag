

- Updates
-  Apple Intelligence updates 

Article

# Apple Intelligence updates

Learn about important changes to Apple Intelligence.

## Overview

Browse notable changes in Apple Intelligence.

## February 2025

- Use ImageCreator to generate images programmatically from your app on devices that support the capability. The system’s generative models use your provided description to generate one or more images and return them to your code. The ImagePlaygroundConcept type includes text you use to describe the image you wish to create, and ImagePlaygroundStyle sets the style to apply to that image.

- Learn how to Enabling Apple Intelligence summarization and prioritization using a Spotlight delegate app extension in your app.

- Learn about Adopting Smart Reply in your messaging or email app to give Apple Intelligence the context of your messaging or mail thread, and insert the generated response back into your app’s UI. Use UIMessageConversationContext for messaging, and UIMailConversationContext for email.

## January 2025

Writing Tools in UIKit:

- Display a bar button item to launch Writing Tools using UIBarButtonItem.SystemItem.writingTools.

- Integrate Writing Tools into your custom text engine using the API in Writing Tools.

Writing Tools in AppKit:

- Display a toolbar item to launch Writing Tools using writingToolsItemIdentifier.

- Integrate Writing Tools into your custom text engine using the API in Writing Tools.

## November 2024

- Make onscreen content available to Siri and Apple Intelligence with App Intents. Describe content as an AppEntity and adopt an assistant schema. Conform the entity to the Transferable protocol, and associate it with a NSUserActivity using the activity’s appEntityIdentifier property.

## July 2024

Note

Testing and using Apple Intelligence features requires iOS 18.1 or later, or macOS 15.1 or later.

### Writing Tools

- In SwiftUI, adjust the level of support for Writing Tools features using the writingToolsBehavior(_:) modifier on the Text, TextField, and TextEditor types.

- In UIKit, detect activity using new UITextViewDelegate methods. Set your text view’s level of support for Writing Tools features using the writingToolsBehavior property of UITextInputTraits.

- In AppKit, detect activity using new NSTextViewDelegate methods. Set your text view’s level of support for Writing Tools features using the writingToolsBehavior property of NSTextInputTraits.

### Genmoji

- Handle Genmoji in text content using NSAdaptiveImageGlyph.

### Siri and App Intents

- Conform your AppIntent, AppEntity, and AppEnum implementations to the assistant schemas by applying the relevant macros to your types.

### Core Spotlight

- Search your indexed content for items that are similar in meaning to the query string, but not necessarily a lexical match, using CSUserQuery. Disable this semantic search support using the disableSemanticSearch property of CSUserQueryContext.

## See Also

### Technology updates

Accelerate updates

Learn about important changes to Accelerate.

Accessibility updates

Learn about important changes to Accessibility.

ActivityKit updates

Learn about important changes in ActivityKit.

AdAttributionKit Updates

Learn about important changes to AdAttributionKit.

App Intents updates

Learn about important changes in App Intents.

AppKit updates

Learn about important changes to AppKit.

Apple Pencil updates

Learn about important changes to Apple Pencil.

ARKit updates

Learn about important changes to ARKit.

Audio Toolbox updates

Learn about important changes to Audio Toolbox.

AuthenticationServices updates

Learn about important changes to AuthenticationServices.

AVFAudio updates

Learn about important changes to AVFAudio.

AVFoundation updates

Learn about important changes to AVFoundation.

Bundle Resources updates

Learn about important changes to Bundle Resources.

ContactsUI updates

Learn about important changes to ContactsUI.

Core Location updates

Learn about important changes to Core Location.

