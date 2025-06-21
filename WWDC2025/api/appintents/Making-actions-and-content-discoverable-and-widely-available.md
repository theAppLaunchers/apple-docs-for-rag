*   [App Intents](/documentation/appintents)
*   Making actions and content discoverable and widely available

Article

# Making actions and content discoverable and widely available

Adopt App Intents to make your app discoverable with Spotlight, controls, widgets, and the Action button.

## [Overview](/documentation/AppIntents/Making-actions-and-content-discoverable-and-widely-available#Overview)

The App Intents framework offers functionality to express your app’s actions and data in a way that enables deep integration with system capabilities Apple Intelligence provides and system experiences like Spotlight. Use App Intents to enable people to view your app’s content and to use its actions when and where they need them — whether they’re using your app or are elsewhere in the system.

The App Intents API is a fundamental framework that facilitates deep integration with system experiences across platforms and devices. You use the framework to express data and actions once to build a reusable foundation for many experiences and features. For example, use App Intents to integrate your app with Siri and Apple Intelligence, then reuse the code to create controls and interactive widgets in combination with [WidgetKit](/documentation/WidgetKit).

Note

Siri’s personal context understanding, onscreen awareness, and in-app actions are in development and will be available with a future software update.

### [Review experiences that App Intents enables directly](/documentation/AppIntents/Making-actions-and-content-discoverable-and-widely-available#Review-experiences-that-App-Intents-enables-directly)

When you use the App Intents framework to express your app’s actions and data, you integrate your app with system experiences that offer broad visibility for your app and content and make its functionality available outside of the app itself; for example:

*   People will use Siri to perform app actions.
    
*   People find App Shortcuts you create in the Shortcuts app and initiate them throughout the system, across platforms and devices with Siri, Spotlight, the Action button, Apple Pencil Pro, and more.
    
*   Using the Shortcuts app, people create custom shortcuts with your app’s functionality and entirely new workflows across apps.
    
*   People reduce distractions with Focus, and you use the App Intents framework to respond to Focus changes.
    

On supported devices, the App Intents framework will provide integration with Apple Intelligence, a personal intelligence system that deeply integrates powerful generative models into the core of iPhone, iPad, and Mac. Siri will draw on the capabilities of Apple Intelligence to deliver assistance that’s natural, contextually relevant, and personal for everyone, including in the apps they use every day. The App Intents framework will enable you to express your app’s capabilities and content, giving the system access to this context and integrating your app with Siri and Apple Intelligence, and unlocking new ways for people to interact with it from anywhere on their device. For more information, refer to [Integrating actions with Siri and Apple Intelligence](/documentation/appintents/integrating-actions-with-siri-and-apple-intelligence) and [Making onscreen content available to Siri and Apple Intelligence](/documentation/appintents/making-onscreen-content-available-to-siri-and-apple-intelligence).

### [Understand experiences that use App Intents API](/documentation/AppIntents/Making-actions-and-content-discoverable-and-widely-available#Understand-experiences-that-use-App-Intents-API)

Across devices, your app’s content and actions appear in additional system experiences you create with a combination of the App Intents framework and other frameworks. As a result, adopting App Intents not only helps you adopt features the framework enables directly, it allows you to easily support additional system experiences that increase your app’s reach and allow people to personalize how they use your app. Use the App Intents framework to describe actions and content together with:

*   [WidgetKit](/documentation/WidgetKit) to offer interactive and configurable widgets, watch complications, and controls
    
*   [ActivityKit](/documentation/ActivityKit) to offer interactive Live Activities
    
*   [Core Spotlight](/documentation/CoreSpotlight) to enable people to find your content using semantic search in Spotlight
    

### [Plan App Intents framework adoption](/documentation/AppIntents/Making-actions-and-content-discoverable-and-widely-available#Plan-App-Intents-framework-adoption)

If you’re new to the App Intents framework, first evaluate your app’s functionality and content. The framework is a fundamental building block for apps, and enables a broad range of user experiences, so it’s important to design a new app with App Intents functionality in mind. Similarly, consider a measured, thoughtful approach when adopting App Intents in your existing app.

To get started:

1.  Understand the role of the App Intents framework and the experiences it enables.
    
2.  Review key framework concepts and create a first implementation that launches your app with an [`AppIntent`](/documentation/appintents/appintent) and add an App Shortcut. For more information, see [Creating your first app intent](/documentation/appintents/creating-your-first-app-intent) and [App Shortcuts](/documentation/appintents/app-shortcuts).
    
3.  Express additional actions and content using the App Intents framework.
    
4.  Integrate actions and content with Siri and Apple Intelligence. For more information, see [App intent domains](/documentation/appintents/app-intent-domains) and [Integrating actions with Siri and Apple Intelligence](/documentation/appintents/integrating-actions-with-siri-and-apple-intelligence).
    
5.  Depending on your app’s functionality, add support for additional system experiences and interactions that fit your app’s functionality. For example, respond to Focus changes as described in [Focus](/documentation/appintents/focus) or add support for the Action button and squeeze gestures on Apple Pencil Pro, as described in [Responding to the Action button on Apple Watch Ultra](/documentation/appintents/actionbuttonarticle).
    

### [Expand existing App Intents usage](/documentation/AppIntents/Making-actions-and-content-discoverable-and-widely-available#Expand-existing-App-Intents-usage)

If you’re currently using the App Intents framework in your app, you might limit app intents to selected actions and content. The App Intents framework will provide integration with Siri and Apple Intelligence for every action of your app and its content. Review your app’s actions and content, and consider expressing actions and content with App Intents.

### [Understand the impact of removing app intents and shortcuts](/documentation/AppIntents/Making-actions-and-content-discoverable-and-widely-available#Understand-the-impact-of-removing-app-intents-and-shortcuts)

People use app intents to automate workflows with custom shortcuts and [App Shortcuts](/documentation/appintents/app-shortcuts). As a result, removing [`AppIntent`](/documentation/appintents/appintent) code or an App Shortcut from your app can break people’s workflows and confuse or frustrate them because previously available functionality might stop working. Keep this in mind when you adopt the App Intents framework and consider a deprecation strategy for your [`AppIntent`](/documentation/appintents/appintent) code. When you plan to remove an [`AppIntent`](/documentation/appintents/appintent), give people notice about your intention to remove the app intent. Publish a release where you change an existing [`AppIntent`](/documentation/appintents/appintent) to [`DeprecatedAppIntent`](/documentation/appintents/deprecatedappintent) and offer people a suggested replacement. After giving people enough time to update their custom shortcuts and move to new App Shortcuts, remove the [`DeprecatedAppIntent`](/documentation/appintents/deprecatedappintent) from your app.

### [Know when to migrate to the App Intents framework](/documentation/AppIntents/Making-actions-and-content-discoverable-and-widely-available#Know-when-to-migrate-to-the-App-Intents-framework)

For new functionality, use the App Intents framework to integrate your app with system experiences like widgets, controls, and Live Activities. Siri and Apple Intelligence automatically will leverage SiriKit intents. For existing functionality keep existing SiriKit implementations and take a measured approach to replacing SiriKit code with App Intents. If you remove code that uses SiriKit, give people advance notice about changes to avoid breaking their existing custom shortcuts and make sure to provide the same or comparable functionality that uses App Intents.

For more information about migrating your SiriKit code to App Intents, see - [Soup Chef with App Intents: Migrating custom intents](/documentation/SiriKit/soup-chef-with-app-intents-migrating-custom-intents).

## [See Also](/documentation/AppIntents/Making-actions-and-content-discoverable-and-widely-available#see-also)

### [Essentials](/documentation/AppIntents/Making-actions-and-content-discoverable-and-widely-available#Essentials)

[

App Intents updates](/documentation/Updates/AppIntents)

Learn about important changes in App Intents.

[

Creating your first app intent](/documentation/appintents/creating-your-first-app-intent)

Create your first app intent that makes your app available in system experiences like Spotlight or the Shortcuts app.

[

Adopting App Intents to support system experiences](/documentation/appintents/adopting-app-intents-to-support-system-experiences)

Create app intents and entities to incorporate system experiences such as Spotlight, visual intelligence, and Shortcuts.

[

Accelerating app interactions with App Intents](/documentation/appintents/acceleratingappinteractionswithappintents)

Enable people to use your app’s features quickly through Siri, Spotlight, and Shortcuts.