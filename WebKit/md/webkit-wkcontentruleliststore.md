

- WebKit
-  WKContentRuleListStore 

Class

# WKContentRuleListStore

An object that contains the rules for how to load and filter content in the web view.

iOS 11.0+iPadOS 11.0+Mac Catalyst 13.1+macOS 10.13+visionOS 1.0+

``` source
@MainActor
class WKContentRuleListStore
```

## Overview

Use a WKContentRuleListStore to compile and manage rules for filtering content in a web view. Rule lists act as content blockers inside your app. You use them to prevent the web view from loading specific content, either based on the original location of that content or other criteria you specify. For example, a corporate app might use rules to prevent the web view from loading content that originates from outside the corporate network.

Fetch the default WKContentRuleListStore object or create a custom store object and use it to compile or access the available rules. Each store object stores its existing rules persistently in the file system and loads those rules at creation time. A store object doesn’t automatically apply any of its rules to a particular web view. To apply a rule to a web view, add it to the WKUserContentController object of the web view’s configuration object.

## Topics

### Creating a Content Rule List Store

class func `default`() -> Self!

Returns the default content rule list store.

convenience init!(url: URL!)

Creates a new content rule list store in the specified directory.

### Creating and Deleting Content Rule Lists

func compileContentRuleList(forIdentifier: String!, encodedContentRuleList: String!, completionHandler: ((WKContentRuleList?, (any Error)?) -> Void)!)

Compiles the specified JSON content into a new rule list and adds it to the current data store.

func removeContentRuleList(forIdentifier: String!, completionHandler: (((any Error)?) -> Void)!)

Removes a rule list from the current data store asynchronously.

### Accessing the Current Rule Lists

func getAvailableContentRuleListIdentifiers((([String]?) -> Void)!)

Fetches the identifiers for all rule lists in the store asynchronously.

func lookUpContentRuleList(forIdentifier: String!, completionHandler: ((WKContentRuleList?, (any Error)?) -> Void)!)

Searches asynchronously for a specific rule list in the data store.

## Relationships

### Inherits From

- NSObject

### Conforms To

- CVarArg
- CustomDebugStringConvertible
- CustomStringConvertible
- Equatable
- Hashable
- NSObjectProtocol
- Sendable

## See Also

### Page Content

class WKUserContentController

An object for managing interactions between JavaScript code and your web view, and for filtering content in your web view.

class WKContentWorld

An object that defines a scope of execution for JavaScript code, and which you use to prevent conflicts between different scripts.

class WKFrameInfo

An object that contains information about a frame on a webpage.

class WKSecurityOrigin

An object that identifies the origin of a particular resource.

class WKUserScript

A script that the web view injects into a webpage.

