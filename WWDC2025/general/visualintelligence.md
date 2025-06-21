Framework

# Visual Intelligence

Include your app’s content in search results that visual intelligence provides.

iOS 26.0+BetaiPadOS 26.0+BetaMac Catalyst 26.0+Beta

## [Overview](/documentation/VisualIntelligence#overview)

![The visual intelligence icon in front of a colorful background.](https://docs-assets.developer.apple.com/published/3bd1138a2956a5abd6c5ad786af48472/visual-intelligence%402x.png)

People use visual intelligence to learn about places and objects around them and onscreen. By pointing their visual intelligence camera at their surroundings and tapping the search button, or by selecting objects in a screenshot, people can search for matching content in apps that offer integration with visual intelligence. Matches appear in the visual intelligence experience, allowing people to view and open items, or see additional search results in the corresponding app. For example, an app that provides information about landmarks might integrate with visual intelligence to allow people to view information about a landmark or open the app for more information.

To integrate your app with visual intelligence and include your app’s content in search results, use the Visual Intelligence framework and [App Intents](/documentation/AppIntents). The Visual Intelligence framework provides you with information captured by visual intelligence, and your app uses the App Intents framework to receive the information and return matching content to the system and visual intelligence.

## [Topics](/documentation/VisualIntelligence#topics)

### [Essentials](/documentation/VisualIntelligence#Essentials)

[

Integrating your app with visual intelligence](/documentation/visualintelligence/integrating-your-app-with-visual-intelligence)

Enable people to find app content that matches their surroundings or objects onscreen with visual intelligence.

```swift
```swift
```swift
struct SemanticContentDescriptor
```
```

A type that represents a scene that visual intelligence captures, like a screenshot, photo, or photo and video stream.
```

### [App intents essentials](/documentation/VisualIntelligence#App-intents-essentials)

[

Making actions and content discoverable and widely available](/documentation/AppIntents/Making-actions-and-content-discoverable-and-widely-available)

Adopt App Intents to make your app discoverable with Spotlight, controls, widgets, and the Action button.

[

Creating your first app intent](/documentation/AppIntents/Creating-your-first-app-intent)

Create your first app intent that makes your app available in system experiences like Spotlight or the Shortcuts app.

Beta Software

This documentation contains preliminary information about an API or technology in development. This information is subject to change, and software implemented according to this documentation should be tested with final operating system software.

[Learn more about using Apple's beta software](https://developer.apple.com/support/beta-software/)