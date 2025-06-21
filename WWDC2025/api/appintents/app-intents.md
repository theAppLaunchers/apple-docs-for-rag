Collection

*   [App Intents](/documentation/appintents)
*   App intents

API Collection

# App intents

Define the custom actions your app exposes to the system, and incorporate support for existing SiriKit intents.

## [Overview](/documentation/AppIntents/app-intents#Overview)

Use app intents to express your app’s capabilities to the system. An app intent includes the code you need to perform an action, and expresses the data you require from the system. The system exposes your actions directly from the Shortcuts app and in system experiences like Siri.

To define an action, create a type that adopts the [`AppIntent`](/documentation/appintents/appintent) protocol, or a related protocol that provides the specific behavior you need. Annotate any key properties with the `@Parameter` property wrapper to let the system know you need the associated information to perform the action.

For more information about features App Intents enables, see [Making actions and content discoverable and widely available](/documentation/appintents/making-actions-and-content-discoverable-and-widely-available).

## [Topics](/documentation/AppIntents/app-intents#topics)

### [Actions](/documentation/AppIntents/app-intents#Actions)

```swift
```swift
```swift
```swift
protocol AppIntent
```
```

An interface for providing an app-specific capability that people invoke from system experiences like Siri and the Shortcuts app.
```
```swift
```swift
```swift
protocol AudioPlaybackIntent
```
```

An App Intent that plays, pauses, or otherwise modifies audio playback state when it executes.
```
```swift
```swift
```swift
protocol AudioRecordingIntent
```
```

An app intent that starts, stops or otherwise modifies audio recording state.
```
```swift
```swift
```swift
protocol AudioStartingIntent
```
```

An App Intent that plays, pauses, or otherwise modifies audio playback state when it executes.

Deprecated
```
```swift
```swift
```swift
protocol CameraCaptureIntent
```
```

Designates intent that will launch an activity that uses device’s camera to capture photos or videos. Marking your intent with this protocol makes it available as a possible action for Camera quick action.
```
```swift
```swift
```swift
protocol DeleteIntent
```
```

Delete the associated entity(s).
```
```swift
```swift
```swift
protocol DeprecatedAppIntent
```
```

An app intent that marks an action as deprecated and informs people which action to use instead.
```
```swift
```swift
```swift
protocol ForegroundContinuableIntent
```
```

A protocol you use for app intents which begin their work with the app in the background but may request to continue in the foreground.

Deprecated
```
```swift
```swift
```swift
protocol OpenIntent
```
```

Open the associated item.
```
```swift
```swift
```swift
struct OpenURLIntent
```
```

An intent that opens a universal link.
```
```swift
```swift
```swift
protocol PlayVideoIntent
```
```

An intent that looks for videos based on a search term, then plays the content.
```
```swift
```swift
```swift
protocol ProgressReportingIntent
```
```

An intent that reports progress to the system during its execution
```
```swift
```swift
```swift
protocol PushToTalkTransmissionIntent
```
```

An intent that begins or ends an audio transmission with the Push to Talk framework.
```
```swift
```swift
```swift
protocol URLRepresentableIntent
```
```

An app intent with a URL representation.
```
```swift
```swift
```swift
protocol SetValueIntent
```
```

An intent that contains a value which can be set.
```
```swift
```swift
```swift
protocol ShowInAppSearchResultsIntent
```
```

An app intent that takes a person to search results for a specified search term.
```
```swift
```swift
```swift
protocol SystemIntent
```
```

Designates intent types provided by App Intents.
```
```

### [Controls, widgets, and Live Activities](/documentation/AppIntents/app-intents#Controls-widgets-and-Live-Activities)

```swift
```swift
```swift
```swift
protocol ControlConfigurationIntent
```
```

An interface for configuring a Control Center module.
```
```swift
```swift
```swift
protocol LiveActivityStartingIntent
```
```

An intent that starts, pauses, or otherwise modifies a Live Activity.

Deprecated
```
```swift
```swift
```swift
protocol LiveActivityIntent
```
```

An intent that starts, pauses, or otherwise modifies a Live Activity when it runs.
```
```swift
```swift
```swift
protocol WidgetConfigurationIntent
```
```

An interface for configuring a WidgetKit widget.
```
```

### [Siri and Apple Intelligence](/documentation/AppIntents/app-intents#Siri-and-Apple-Intelligence)

[

Integrating actions with Siri and Apple Intelligence](/documentation/appintents/integrating-actions-with-siri-and-apple-intelligence)

Create app intents, entities, and enumerations that conform to assistant schemas to tap into the enhanced action capabilities of Siri and Apple Intelligence.

[

API Reference

App intent domains](/documentation/appintents/app-intent-domains)

Make your app’s actions and content available to Siri and Apple Intelligence with assistant schemas.

### [SiriKit intent migration](/documentation/AppIntents/app-intents#SiriKit-intent-migration)

```swift
```swift
```swift
```swift
protocol CustomIntentMigratedAppIntent
```
```

An interface for replacing a custom SiriKit intent that allows existing shortcuts and donations to continue working.
```
```

### [Dependency management](/documentation/AppIntents/app-intents#Dependency-management)

```swift
```swift
```swift
```swift
class AppDependencyManager
```
```

An object that manages the registration and initialization of an app intent’s dependencies.
```
```swift
```swift
```swift
class AppDependency
```
```

A property wrapper that resolves a registered dependency at runtime.
```
```

### [Supplementary content](/documentation/AppIntents/app-intents#Supplementary-content)

```swift
```swift
```swift
```swift
protocol AppIntentsPackage
```
```

A type that describes app intent definitions that aren’t part of an app bundle and their dependencies.
```
```swift
```swift
```swift
struct IntentDescription
```
```

The human-readable description and metadata for an app intent.
```
```swift
```swift
```swift
struct IntentDialog
```
```

The text you want the system to display, or speak, when requesting a value, asking for disambiguation, or confirming an action.
```
```swift
```swift
```swift
struct IntentDeprecation
```
```
```
```swift
```swift
```swift
class IntentProjection
```
```

Projections for an app intent that returns non-optional values for parameters.
```
```swift
```swift
```swift
struct IntentSystemContext
```
```

Information that the system makes available to an app intent while it performs its action.
```
```

### [Results](/documentation/AppIntents/app-intents#Results)

```swift
```swift
```swift
```swift
protocol IntentResult
```
```

A type that contains the result of performing an action, and includes optional information to deliver back to the initiator.
```
```swift
```swift
```swift
struct IntentResultContainer
```
```

An object that represents the output of a completed intent.
```
```swift
```swift
```swift
protocol OpensIntent
```
```

The result of performing an action that delivers an app intent back to the initiator of the action.
```
```swift
```swift
```swift
protocol ProvidesDialog
```
```

The result of performing an action that delivers a dialog back to the initiator of the action.
```
```swift
```swift
```swift
protocol ReturnsValue
```
```

The result of performing an action that delivers a value back to the initiator.
```
```swift
```swift
```swift
protocol ShowsSnippetView
```
```

The result of performing an action that delivers a view back to the initiator of the action.
```
```swift
```swift
```swift
protocol ResultsCollection
```
```

A protocol representing a collection of returned items with support for sectioning.
```
```

### [Extensions](/documentation/AppIntents/app-intents#Extensions)

```swift
```swift
```swift
```swift
protocol AppIntentsExtension
```
```

An interface for managing an extension’s configuration.
```
```

## [See Also](/documentation/AppIntents/app-intents#see-also)

### [Actions](/documentation/AppIntents/app-intents#Actions)

[

API Reference

Intent discovery](/documentation/appintents/intent-discovery)

Donate your app’s intents to the system to help it identify trends and predict future behaviors.

[

API Reference

App Shortcuts](/documentation/appintents/app-shortcuts)

Integrate your app’s intents and entities with the Shortcuts app, Siri, Spotlight, and the Action button on supported iPhone and Apple Watch models.