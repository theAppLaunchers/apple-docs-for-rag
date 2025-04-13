

- Safari Services
-  Safari app extensions 

API Collection

# Safari app extensions

Learn how Safari app extensions extend the web-browsing experience in Safari by leveraging web technologies and native code.

## Overview

A Safari app extension can add new functionality to Safari by reading and modifying webpage content. These capabilities enhance the tools you use, the tasks you can accomplish, and the data you can access in your browser. A Safari app extension is uniquely useful because it can communicate with a native app. Sharing data between an app and Safari lets you integrate app content into Safari or send web data back to the app, enabling a unified experience for a web version and a native version of an app.

Note

Previously, Safari extensions provided the communication between apps and Safari. To migrate a legacy Safari extension, see Converting a legacy Safari extension to a Safari app extension.

Safari app extensions use a combination of JavaScript, CSS, and native code written in Objective-C or Swift. Because you build Safari app extensions on the standard app extension model, you get many native app benefits:

- You bundle Safari app extensions inside your app and distribute them through the App Store. You can distribute a Safari app extension with a Mac app or a Mac Catalyst app.

- Because you distribute your app and your Safari app extension together, you minimize the chances of installing mismatched versions.

- Your Safari app extension can securely communicate with your app using shared resources.

To become familiar with app extension concepts, see App Extensions. If you’re interested in deploying an extension you build for Chrome, Firefox, or Edge in Safari, or creating an extension that works in Safari and other browsers, see Safari web extensions.

## Topics

### Essentials

Building a Safari app extension

Add, build, and enable a Safari app extension.

Converting a legacy Safari extension to a Safari app extension

Convert a legacy Safari extension to a Safari app extension, automatically with keys or manually.

Troubleshooting your Safari app extension

Debug your Safari app extension with these techniques.

### Injected style sheets and scripts

Add, control, and update settings for injected style sheets and scripts in a Safari app extension.

Using injected style sheets and scripts

Learn how you can affect the appearance or behavior of a webpage by using injected style sheets and scripts.

Injecting a script into a webpage

Inject a script that you write for a Safari app extension into a webpage.

Injecting CSS style sheets into a webpage

Add to or override styles by injecting CSS style sheets into webpages.

Passing messages between Safari app extensions and injected scripts

Communicate between your Safari app extension and injected scripts.

class SFSafariExtensionHandler

A base class that you subclass to handle events in your Safari app extension.

class SFSafariExtensionManager

A class that your app uses to find out the current state of a Safari app extension.

class SFSafariExtensionState

The state of a Safari app extension.

class SFSafariPageProperties

An object that captures information about a webpage.

protocol SFSafariExtensionHandling

A protocol for implementing event handling in a Safari app extension.

let SFExtensionProfileKey: String

A string the system uses as a key in a user info dictionary to identify a profile identifier.

### Information property list keys

Safari app extension information property list keys

Specify keys in your information property list file that provide information about your Safari app extension, UI, and permissions to the operating system.

## See Also

### Related Documentation

Safari Extensions JS

Communicate with your native extension from your Safari app extension, and support delivery of push notifications in Safari.

Safari web extensions

Create web extensions that work in Safari and other browsers.

### Safari app extensions

class SFSafariExtension

A proxy for the Safari extension.

class SFSafariApplication

A proxy for the Safari app.

class SFSafariWindow

A proxy for a Safari window.

class SFSafariPage

A proxy for a Safari webpage.

class SFSafariTab

A proxy for a tab in a Safari window.

