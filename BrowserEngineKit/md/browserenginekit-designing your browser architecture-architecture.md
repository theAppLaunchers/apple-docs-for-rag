

- BrowserEngineKit
-  Designing your browser architecture 

Article

# Designing your browser architecture

Isolate privileged access to operating system resources and private data from untrusted code.

## Overview

A browser is a complex app with many components: a graphical user interface (GUI), network communications, media playing, content parsing and rendering, and JavaScript execution. Improve the security of your browser for people using your app by creating separate extensions that are responsible for different parts of your app. The operating system runs your app and each of its extensions in separate processes with their own sandboxed access to operating system resources. Communicate between your app and its extensions, and between extensions, using XPC.

## Present the GUI and handle user input

Your app presents the browser GUI, handles input from the person using the browser, and coordinates with the extensions to provide the browser features. Use SwiftUI or UIKit to display user interface and handle input. For more information on managing extensions, see Managing the browser extension life cycle.

Use other API as necessary to provide common app features, for example, store a person’s preferences with UserDefaults.

Note

A browser app has a restricted app sandbox that stops the app from accessing some APIs. Your app can’t get the advertisingIdentifier, and can’t detect the presence of other apps using canOpenURL(_:).

If your browser engine uses custom text rendering and layout routines to display text on a web page, your browser app needs to adopt UITextInput and `BETextInput` to integrate with standard text interactions like showing text selection and displaying the contextual menu.

## Create a networking extension

Your browser can create one instance of a networking extension, which uses NSURLSession or socket APIs to retrieve remote resources and submit HTTP POST data. When web content extensions need to fetch additional resources, for example, images referenced in HTML documents, they communicate with the network extension to make the request and retrieve the data.

## Create content extensions

You create a content extension to host your browser’s rendering engine, which parses HTML documents and CSS style sheets, runs Javascript, and prepares the resulting document object for display. Create as many content extensions as your app needs to securely process browser contents, for example, one extension for each browser tab that a person uses, or one extension for each document and iframe with which your app works.

Content extensions work with untrusted data from remote sources, so don’t access a person’s data or operating system resources from a content extension. Instead, design protocols for communicating between your content extensions and your browser app and the other extensions that permit limited requests to access specific resources.

If your content extension uses just-in-time (JIT) compilation to run JavaScript code, you need to toggle the memory that contains the compiled code from writable to executable. For more information, see Protecting code compiled just in time.

## Process video and graphics

Your browser can create one instance of a rendering extension, which uses Metal to directly access the GPU to process video and other complex graphical data.

The operating system maintains a low level for the maximum memory that the rendering extension may allocate. If your rendering extension uses more than the permitted maximum memory, the operating system may stop the extension. To avoid requesting too much memory in the rendering extension, your content extension can claim ownership of memory that the rendering extension uses to render its content. For more information, see Attributing memory to a content extension.

## See Also

### Essentials

Developing a browser app that uses an alternative browser engine

Create a web browser app and associated extensions.

Preparing your app to be the default web browser

Configure your browser app so users can set it as the default on their device instead of Safari.

