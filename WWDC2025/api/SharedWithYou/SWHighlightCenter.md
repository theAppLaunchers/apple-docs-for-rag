*   [SharedWithYou](/documentation/sharedwithyou)
*   SWHighlightCenter

Class

# SWHighlightCenter

An object that contains a priority-ordered list of universal links to share with the current user.

iOS 16.0+iPadOS 16.0+Mac Catalyst 16.0+macOS 13.0+tvOS 16.0+visionOS 1.0+

```swift
```swift
```swift
```swift
```swift
```swift
```swift
```swift
class SWHighlightCenter
```
```
```
```
```
```
```
```

## [Mentioned in](/documentation/SharedWithYou/SWHighlightCenter#mentions)

[

Adding custom collaboration to your app](/documentation/sharedwithyou/adding-custom-collaboration-to-your-app)

[

Adding shared content collaboration to your app](/documentation/sharedwithyou/adding-shared-content-collaboration-to-your-app)

[

Making your app content shareable](/documentation/sharedwithyou/making-your-app-content-shareable)

## [Overview](/documentation/SharedWithYou/SWHighlightCenter#overview)

The system determines which links it surfaces. The app is responsible for updating its UI to reflect the latest highlights list that the system provides.

## [Topics](/documentation/SharedWithYou/SWHighlightCenter#topics)

### [Setting the delegate](/documentation/SharedWithYou/SWHighlightCenter#Setting-the-delegate)

```swift
```swift
```swift
```swift
var delegate: (any SWHighlightCenterDelegate)?
```
```

The delegate object for the highlight center.
```
```swift
```swift
```swift
protocol SWHighlightCenterDelegate
```
```

The protocol you use to notify the delegate when the list or rank order of surfaced highlights changes.
```
```

### [Accessing highlights](/documentation/SharedWithYou/SWHighlightCenter#Accessing-highlights)

```swift
```swift
```swift
```swift
var highlights: [SWHighlight]
```
```

An array of shared highlights.
```
```swift
```swift
```swift
class var highlightCollectionTitle: String
```
```

A localized title to display with a collection of highlights.
```
```

### [Retrieving collaboration highlights](/documentation/SharedWithYou/SWHighlightCenter#Retrieving-collaboration-highlights)

```swift
```swift
```swift
```swift
class var isSystemCollaborationSupportAvailable: Bool
```
```

A Boolean value that represents full support for Messages collaboration features.
```
```swift
```swift
```swift
func collaborationHighlight(forIdentifier: SWCollaborationIdentifier) throws -> SWCollaborationHighlight
```
```

Returns a collaboration highlight for a specified collaboration identifier.
```
```swift
```swift
```swift
func collaborationHighlight(forIdentifier: String) throws -> SWCollaborationHighlight
```
```

Returns a collaboration highlight for a specified identifier string.
```
```swift
```swift
```swift
func getCollaborationHighlight(for: URL, completionHandler: (SWCollaborationHighlight?, (any Error)?) -> Void)
```
```

Returns a collaboration highlight for a specified URL.
```
```swift
```swift
```swift
func getHighlightFor(URL, completionHandler: (SWHighlight?, (any Error)?) -> Void)
```
```

Returns a highlight for a specified URL.
```
```swift
```swift
```swift
func getSignedIdentityProof(for: SWCollaborationHighlight, using: Data, completionHandler: (SWPerson.SignedIdentityProof?, (any Error)?) -> Void)
```
```

Signs passed-in data with the local device’s private key.
```
```

### [Posting highlight events](/documentation/SharedWithYou/SWHighlightCenter#Posting-highlight-events)

```swift
```swift
```swift
```swift
func postNotice(for: any SWHighlightEvent)
```
```

Posts a specified event to the highlight center for display.
```
```swift
```swift
```swift
func clearNotices(for: SWCollaborationHighlight)
```
```

Clears the notices for a specified collaboration highlight.
```
```

### [Handling errors](/documentation/SharedWithYou/SWHighlightCenter#Handling-errors)

```swift
```swift
```swift
```swift
enum SWHighlightCenterErrorCode
```
```

The error codes for the highlight center.
```
```

## [Relationships](/documentation/SharedWithYou/SWHighlightCenter#relationships)

### [Inherits From](/documentation/SharedWithYou/SWHighlightCenter#inherits-from)

*   [`NSObject`](/documentation/ObjectiveC/NSObject-swift.class)

### [Conforms To](/documentation/SharedWithYou/SWHighlightCenter#conforms-to)

*   [`CVarArg`](/documentation/Swift/CVarArg)
*   [`CustomDebugStringConvertible`](/documentation/Swift/CustomDebugStringConvertible)
*   [`CustomStringConvertible`](/documentation/Swift/CustomStringConvertible)
*   [`Equatable`](/documentation/Swift/Equatable)
*   [`Hashable`](/documentation/Swift/Hashable)
*   [`NSObjectProtocol`](/documentation/ObjectiveC/NSObjectProtocol)

## [See Also](/documentation/SharedWithYou/SWHighlightCenter#see-also)

### [Highlights](/documentation/SharedWithYou/SWHighlightCenter#Highlights)

```swift
```swift
```swift
```swift
class SWHighlight
```
```

An object that represents a universal link to share by any number of contacts in one or more conversations.
```
```