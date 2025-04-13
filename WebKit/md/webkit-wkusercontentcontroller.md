

- WebKit
-  WKUserContentController 

Class

# WKUserContentController

An object for managing interactions between JavaScript code and your web view, and for filtering content in your web view.

iOS 8.0+iPadOS 8.0+Mac Catalyst 13.1+macOS 10.10+visionOS 1.0+

``` source
@MainActor
class WKUserContentController
```

## Overview

A WKUserContentController object provides a bridge between your app and the JavaScript code running in the web view. Use this object to do the following:

- Inject JavaScript code into webpages running in your web view.

- Install custom JavaScript functions that call through to your app’s native code.

- Specify custom filters to prevent the webpage from loading restricted content.

Create and configure a WKUserContentController object as part of your overall web view setup. Assign the object to the userContentController property of your WKWebViewConfiguration object before creating your web view.

## Topics

### Adding and Removing Custom Scripts

func addUserScript(WKUserScript)

Injects the specified script into the webpage’s content.

func removeAllUserScripts()

Removes all user scripts from the web view.

var userScripts: [WKUserScript]

The user scripts associated with the user content controller.

### Adding and Removing Message Handlers

func add(any WKScriptMessageHandler, name: String)

Installs a message handler that you can call from your JavaScript code.

func add(any WKScriptMessageHandler, contentWorld: WKContentWorld, name: String)

Installs a message handler that you can call from the specified content world in your JavaScript code.

func addScriptMessageHandler(any WKScriptMessageHandlerWithReply, contentWorld: WKContentWorld, name: String)

Installs a message handler that returns a reply to your JavaScript code.

func removeScriptMessageHandler(forName: String)

Uninstalls the custom message handler with the specified name from your JavaScript code.

func removeScriptMessageHandler(forName: String, contentWorld: WKContentWorld)

Uninstalls a custom message handler from the specified content world in your JavaScript code.

func removeAllScriptMessageHandlers(from: WKContentWorld)

Uninstalls all custom message handlers from the specified content world in your JavaScript code.

func removeAllScriptMessageHandlers()

Uninstalls all custom message handlers associated with the user content controller.

protocol WKScriptMessageHandler

An interface for receiving messages from JavaScript code running in a webpage.

protocol WKScriptMessageHandlerWithReply

An interface for responding to messages from JavaScript code running in a webpage.

### Adding and Removing Content Rules

func add(WKContentRuleList)

Adds the specified content rule list to the content controller object.

func remove(WKContentRuleList)

Removes the specified rule list from the content controller object.

func removeAllContentRuleLists()

Removes all rules lists from the content controller.

class WKContentRuleList

A compiled list of rules to apply to web content.

## Relationships

### Inherits From

- NSObject

### Conforms To

- CVarArg
- CustomDebugStringConvertible
- CustomStringConvertible
- Equatable
- Hashable
- NSCoding
- NSObjectProtocol
- NSSecureCoding
- Sendable

## See Also

### Page Content

class WKContentRuleListStore

An object that contains the rules for how to load and filter content in the web view.

class WKContentWorld

An object that defines a scope of execution for JavaScript code, and which you use to prevent conflicts between different scripts.

class WKFrameInfo

An object that contains information about a frame on a webpage.

class WKSecurityOrigin

An object that identifies the origin of a particular resource.

class WKUserScript

A script that the web view injects into a webpage.

