Technology

# SiriKit

Empower users to interact with their devices through voice, intelligent suggestions, and personalized workflows.

iOS 10.0+iPadOS 10.0+Mac Catalyst 13.0+macOS 12.0+tvOS 14.0+visionOS 1.0+watchOS 3.2+

## [Overview](/documentation/SiriKit#overview)

The Intents and IntentsUI frameworks drive interactions that start with “Hey Siri…”, Shortcuts actions, and widget configuration. The system also incorporates intents and user activities your app donates into contextual suggestions in Maps, Calendar, Watch complications, widgets, and search results.

![A collection of devices, including a MacBook Air, an iPhone, an Apple Watch, and a HomePod mini. The devices display user interactions that SiriKit enables. On the MacBook Air, the Shortcuts app is open with a collection of shortcuts in the All Shortcuts section. The iPhone displays a Siri Suggestion with the Maps icon. The Apple Watch displays the Siri animation and the words “What can I help you with?”](https://docs-assets.developer.apple.com/published/06419e94cd4dfe4473c92e9964f7377f/media-3849683%402x.png)

Use the standard intents that the system provides to empower actions users already ask Siri to do, such as playing music or sending a text message. You can also offer your app’s unique capabilities throughout the system by designing custom intents. For more details about defining custom intents, see [Adding User Interactivity with Siri Shortcuts and the Shortcuts App](/documentation/SiriKit/adding-user-interactivity-with-siri-shortcuts-and-the-shortcuts-app).

You can process intents directly in your app, or in an Intents app extension. For guidance on setting up an app extension and sharing information between your app and extension, see [Structuring Your Code to Support App Extensions](/documentation/SiriKit/structuring-your-code-to-support-app-extensions).

To display branding or other customized content in Siri and Maps after you fulfill a user request, create a custom view controller in an IntentsUI app extension. See [Creating an Intents UI Extension](/documentation/sirikit/creating-an-intents-ui-extension) for more details.

Important

With a person’s permission, an installed health research app that uses [SensorKit](/documentation/SensorKit) entitlements may collect Face Metrics data while your SiriKit app is in use. To prevent SensorKit from collecting Face Metrics data while your app is in use, you can set the [`SRResearchDataGeneration`](/documentation/BundleResources/Information-Property-List/SRResearchDataGeneration) information property list key to `NO`.

## [Topics](/documentation/SiriKit#topics)

### [Frameworks](/documentation/SiriKit#Frameworks)

Reference the API that compose SiriKit

[

Intents](/documentation/intents)

Empower people to customize interactions for your app on their device.

[

IntentsUI](/documentation/intentsui)

Customize content in the interface for Siri and Maps.

### [Sample code](/documentation/SiriKit#Sample-code)

Browse sample code that walks through specific Intents and IntentsUI workflows.

[

Adding Shortcuts for Wind Down](/documentation/sirikit/adding-shortcuts-for-wind-down)

Reveal your app’s shortcuts inside the Health app.

[

Booking Rides with SiriKit](/documentation/sirikit/booking-rides-with-sirikit)

Add Intents extensions to your app to handle requests to book rides using Siri and Maps.

[

Handling Payment Requests with SiriKit](/documentation/sirikit/handling-payment-requests-with-sirikit)

Add an Intent Extension to your app to handle money transfer requests with Siri.

[

Handling Workout Requests with SiriKit](/documentation/sirikit/handling-workout-requests-with-sirikit)

Add an Intent Extension to your app that handles requests to control workouts with Siri.

[

Integrating Your App with Siri Event Suggestions](/documentation/sirikit/integrating-your-app-with-siri-event-suggestions)

Donate reservations and provide quick access to event details throughout the system.

[

Managing Audio with SiriKit](/documentation/sirikit/managing-audio-with-sirikit)

Control audio playback and handle requests to add media using SiriKit Media Intents.

[

Providing Hands-Free App Control with Intents](/documentation/sirikit/providing-hands-free-app-control-with-intents)

Resolve, confirm, and handle intents without an extension.

[

Soup Chef: Accelerating App Interactions with Shortcuts](/documentation/sirikit/soup-chef-accelerating-app-interactions-with-shortcuts)

Make it easy for people to use Siri with your app by providing shortcuts to your app’s actions.

[

Soup Chef with App Intents: Migrating custom intents](/documentation/sirikit/soup-chef-with-app-intents-migrating-custom-intents)

Integrating App Intents to provide your appʼs actions to Siri and Shortcuts.

### [Articles](/documentation/SiriKit#Articles)

Browse articles that cover high-level Intents and IntentsUI tasks.

[

Adding User Interactivity with Siri Shortcuts and the Shortcuts App](/documentation/sirikit/adding-user-interactivity-with-siri-shortcuts-and-the-shortcuts-app)

Add custom intents and parameters to help users interact more quickly and effectively with Siri and the Shortcuts app.

[

Defining Relevant Shortcuts for the Siri Watch Face](/documentation/sirikit/defining-relevant-shortcuts-for-the-siri-watch-face)

Inform Siri when your app’s shortcuts may be useful to the user.

[

Deleting Donated Shortcuts](/documentation/sirikit/deleting-donated-shortcuts)

Remove your donations from Siri.

[

Dispatching intents to handlers](/documentation/sirikit/dispatching-intents-to-handlers)

Provide SiriKit with an intent handler capable of handling a specific intent.

[

Improving Siri Media Interactions and App Selection](/documentation/sirikit/improving-siri-media-interactions-and-app-selection)

Fine-tune voice controls and improve Siri Suggestions by sharing app capabilities, customized names, and listening habits with the system.

[

Improving interactions between Siri and your messaging app](/documentation/sirikit/improving-interactions-between-siri-and-your-messaging-app)

Donate app-specific content, use Siri’s contact suggestions, and adopt the latest platform features to create a more consistent messaging experience.

[

API Reference

Registering Custom Vocabulary with SiriKit](/documentation/sirikit/registering-custom-vocabulary-with-sirikit)

Register your app’s custom terminology, and provide sample phrases for how to use your app with Siri.

[

Confirming the Details of an Intent](/documentation/sirikit/confirming-the-details-of-an-intent)

Perform final validation of the intent parameters and verify that your services are ready to fulfill the intent.

[

Handling an Intent](/documentation/sirikit/handling-an-intent)

Fulfill the intent and provide feedback to SiriKit about what you did.

[

Resolving the Parameters of an Intent](/documentation/sirikit/resolving-the-parameters-of-an-intent)

Validate the parameters of an intent and make sure that you have the information you need to continue.

[

Generating a List of Ride Options](/documentation/sirikit/generating-a-list-of-ride-options)

Generate ride options for Maps to display to the user.

[

API Reference

Handling the Ride-Booking Intents](/documentation/sirikit/handling-the-ride-booking-intents)

Support the different intent-handling sequences for booking rides with Shortcuts or Maps.

[

Displaying Shortcut Information in a Siri Watch Face Card](/documentation/sirikit/displaying-shortcut-information-in-a-siri-watch-face-card)

Display and customize watch-specific shortcut information with a default card template.

[

Donating Reservations](/documentation/sirikit/donating-reservations)

Inform Siri of reservations made from your app.

[

Defining Relevant Shortcuts for the Siri Watch Face](/documentation/sirikit/defining-relevant-shortcuts-for-the-siri-watch-face)

Inform Siri when your app’s shortcuts may be useful to the user.

[

Specifying Synonyms for Your App Name](/documentation/sirikit/specifying-synonyms-for-your-app-name)

Provide alternative names for your app that are more familiar or easier for users to speak.

[

Intent Phrases](/documentation/sirikit/intent-phrases)

The keys that you include in your global vocabulary file to show how users engage your app from Siri.

[

Localizing Your Vocabulary for Chinese Dialects](/documentation/sirikit/localizing-your-vocabulary-for-chinese-dialects)

Apply emphasis markers to your pronunciation tips to assist Siri with Chinese dialects.

[

Parameter Vocabularies](/documentation/sirikit/parameter-vocabularies)

The keys you include in your global vocabulary file to describe app-specific terms.

[

Offering Actions in the Shortcuts App](/documentation/sirikit/offering-actions-in-the-shortcuts-app)

Suggest shortcuts users may want to add to Siri or combine with other actions in their own shortcuts.

[

Creating an Intents App Extension](/documentation/sirikit/creating-an-intents-app-extension)

Add and configure an Intents app extension in your Xcode project.

[

Requesting Authorization to Use Siri](/documentation/sirikit/requesting-authorization-to-use-siri)

Request permission from the user for Siri and Maps to communicate with your app or Intents app extension.

[

Structuring Your Code to Support App Extensions](/documentation/sirikit/structuring-your-code-to-support-app-extensions)

Move your back-end services to a private framework so your app and app extensions can use them.

[

Providing Live Status Updates](/documentation/sirikit/providing-live-status-updates)

Provide regular updates to Maps about the status of a booked ride.

[

Donating Shortcuts](/documentation/sirikit/donating-shortcuts)

Tell Siri about shortcuts to actions that the user performed in your app.

[

Configuring the View Controller for Your Custom Interface](/documentation/sirikit/configuring-the-view-controller-for-your-custom-interface)

Configure your view controller to replace or augment the default interface in Siri or Maps.

[

Configuring Your Intents UI App Extension Target](/documentation/sirikit/configuring-your-intents-ui-app-extension-target)

Configure your Xcode project to include an Intents UI app extension that you use to customize the Siri and Maps interfaces.