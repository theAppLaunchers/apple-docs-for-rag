Collection

*   [Safari Services](/documentation/safariservices)
*   Safari web extensions

API Collection

# Safari web extensions

Create web extensions that work in Safari and other browsers.

## [Overview](/documentation/SafariServices/safari-web-extensions#overview)

A Safari web extension adds custom functionality to Safari using JavaScript APIs and common file formats from extensions for Google Chrome, Mozilla Firefox, and Microsoft Edge browsers. While [Safari app extensions](/documentation/safariservices/safari-app-extensions) are useful for sharing code between your native macOS app and Safari, you build Safari web extensions primarily on JavaScript, HTML, and CSS, and can repackage them to work in other browsers. You can also use Safari web extensions in [Mac web apps](https://support.apple.com/en-us/104996).

Important

You implement a Safari web extension as a macOS, visionOS, or iOS app extension to provide a safe and secure distribution and usage model. You can distribute a Safari web extension with a Mac app, a visionOS app, an iOS app, or a Mac app created using [Mac Catalyst](/documentation/UIKit/mac-catalyst). Use [Xcode](https://developer.apple.com/xcode/) to package your extension for testing and distribution, and join the [Apple Developer Program](https://developer.apple.com/programs/) to distribute Safari web extensions. For more information, see [Distributing your Safari web extension](/documentation/safariservices/distributing-your-safari-web-extension).

To get started with creating a Safari web extension, use one of the following options:

*   Convert your existing extension into a Safari web extension, so you can use it in Safari in macOS, visionOS, and iOS and distribute it. Xcode includes a command-line tool to simplify this process.
    
*   Build a new Safari web extension in Xcode using the built-in template. You can then repackage the extension files for deployment in other browsers.
    
*   Temporarily install your web extension in Safari for testing without converting it or setting up an Xcode project. For more information, see [Temporarily install a web extension folder in macOS Safari](/documentation/safariservices/running-your-safari-web-extension#Temporarily-install-a-web-extension-folder-in-macOS-Safari).
    

Learn more about the capabilities of web extensions and the APIs you use to build them in Mozilla’s [Browser Extensions](https://developer.mozilla.org/en-US/docs/Mozilla/Add-ons/WebExtensions) documentation.

Safari web extensions are available in macOS with Safari 14 and later, visionOS 1 and later, and iOS 15 and later. Safari web extensions are available in Mac web apps in macOS 15 and later.

## [Topics](/documentation/SafariServices/safari-web-extensions#topics)

### [New extensions](/documentation/SafariServices/safari-web-extensions#New-extensions)

[

Creating a Safari web extension](/documentation/safariservices/creating-a-safari-web-extension)

Build a Safari web extension in Xcode.

[

Modernizing Safari Web Extensions](/documentation/safariservices/modernizing-safari-web-extensions)

Learn about enhancements to Safari Web Extensions.

[

Developing a Safari Web Extension](/documentation/safariservices/developing-a-safari-web-extension)

Customize and enhance web pages by building a Safari web extension.

### [Extension conversions](/documentation/SafariServices/safari-web-extensions#Extension-conversions)

[

Converting a web extension for Safari](/documentation/safariservices/converting-a-web-extension-for-safari)

Convert your existing extension to a Safari web extension using Xcode’s command-line tool.

[

Converting a Safari app extension to a Safari web extension](/documentation/safariservices/converting-a-safari-app-extension-to-a-safari-web-extension)

Unify your web extensions and simplify development by sharing code with a Safari web extension.

[

Packaging and distributing Safari Web Extensions with App Store Connect](/documentation/safariservices/packaging-and-distributing-safari-web-extensions-with-app-store-connect)

Upload and distribute Safari Web Extensions without using a Mac or Xcode.

### [Extension updates](/documentation/SafariServices/safari-web-extensions#Extension-updates)

[

Updating a Safari web extension](/documentation/safariservices/updating-a-safari-web-extension)

Add new features and fix bugs in your Safari web extension using Xcode tools.

[

Managing Safari web extension permissions](/documentation/safariservices/managing-safari-web-extension-permissions)

Respect user privacy by setting appropriate permissions for your Safari web extension.

[

Previewing Metadata using Open Graph](/documentation/safariservices/previewing-metadata-using-open-graph)

Build a Safari Extension that displays metadata using Open Graph.

### [Messaging](/documentation/SafariServices/safari-web-extensions#Messaging)

[

Messaging between the app and JavaScript in a Safari web extension](/documentation/safariservices/messaging-between-the-app-and-javascript-in-a-safari-web-extension)

Communicate about events and share data between the containing app and JavaScript by using native messaging and app groups.

```swift
```swift
```swift
let SFExtensionMessageKey: String
```
```

A string the system uses as a key in a user info dictionary to identify a message.
```
```swift
```swift
```swift
let SFExtensionProfileKey: String
```
```

A string the system uses as a key in a user info dictionary to identify a profile identifier.
```

[

Messaging a Web Extension’s Native App](/documentation/safariservices/messaging-a-web-extension-s-native-app)

Communicate between your Safari web extension and its containing app.

[

Messaging between a webpage and your Safari web extension](/documentation/safariservices/messaging-between-a-webpage-and-your-safari-web-extension)

Configure your extension to enable messaging from webpages, and then update your extension to handle messages.

### [Blocking content](/documentation/SafariServices/safari-web-extensions#Blocking-content)

[

Blocking content with your Safari web extension](/documentation/safariservices/blocking-content-with-your-safari-web-extension)

Build content blocking with declarative net request into your Safari web extension.

[

Adopting Declarative Content Blocking in Safari Web Extensions](/documentation/safariservices/adopting-declarative-content-blocking-in-safari-web-extensions)

Block web content with your web extension using the declarative net request API.

### [Adding Web Inspector tools](/documentation/SafariServices/safari-web-extensions#Adding-Web-Inspector-tools)

[

Adding a web development tool to Safari Web Inspector](/documentation/safariservices/adding-a-web-development-tool-to-safari-web-inspector)

Expand the built-in Safari Web Inspector to include your custom tool, augmenting developers’ options for inspecting, testing, and debugging webpages.

[

Creating Safari Web Inspector extensions](/documentation/safariservices/creating-safari-web-inspector-extensions)

Learn how to make custom Safari Web Inspector extensions.

### [Extension improvements](/documentation/SafariServices/safari-web-extensions#Extension-improvements)

[

Optimizing your web extension for Safari](/documentation/safariservices/optimizing-your-web-extension-for-safari)

Support Dark Mode, reduce memory and power usage, and ensure feature compatibility to improve your web extension experience in Safari and web apps.

[

Adopting New Safari Web Extension APIs](/documentation/safariservices/adopting-new-safari-web-extension-apis)

Improve your web extension in Safari with a non-persistent background page and new tab-override customization.

[

Syncing Safari web extensions across devices and platforms](/documentation/safariservices/syncing-safari-web-extensions-across-devices-and-platforms)

Let users install your extension on one device and then use and manage the extension on all their other iOS and macOS devices.

[

Assessing your Safari web extension’s browser compatibility](/documentation/safariservices/assessing-your-safari-web-extension-s-browser-compatibility)

Review your Safari web extension implementation plan, manifest keys, and JavaScript API usage for compatibility with other browsers.

[

Troubleshooting your Safari web extension](/documentation/safariservices/troubleshooting-your-safari-web-extension)

Use developer resources to investigate and resolve common problems with Safari web extensions.

### [Installation and distribution](/documentation/SafariServices/safari-web-extensions#Installation-and-distribution)

[

Running your Safari web extension](/documentation/safariservices/running-your-safari-web-extension)

Install and update your extension in Safari as you make changes in development.

[

Distributing your Safari web extension](/documentation/safariservices/distributing-your-safari-web-extension)

Get feedback on your extension from beta testers, then share your extension with customers in the App Store.