*   [SharedWithYou](/documentation/sharedwithyou)
*   SWHighlight

Class

# SWHighlight

An object that represents a universal link to share by any number of contacts in one or more conversations.

iOS 16.0+iPadOS 16.0+Mac Catalyst 16.0+macOS 13.0+tvOS 16.0+visionOS 1.0+

```swift
```swift
```swift
```swift
```swift
```swift
```swift
```swift
class SWHighlight
```
```
```
```
```
```
```
```

## [Mentioned in](/documentation/SharedWithYou/SWHighlight#mentions)

[

Adding shared content collaboration to your app](/documentation/sharedwithyou/adding-shared-content-collaboration-to-your-app)

[

Making your app content shareable](/documentation/sharedwithyou/making-your-app-content-shareable)

## [Overview](/documentation/SharedWithYou/SWHighlight#overview)

The system doesn’t expose the identities of the contacts to the app. It tracks shared universal links for the current user and determines which links to elevate for consumption in an app. When the system deems a link to be useful, it surfaces that link to the hosting app in the form of an `SWHighlight` object.

## [Topics](/documentation/SharedWithYou/SWHighlight#topics)

### [Viewing highlight attributes](/documentation/SharedWithYou/SWHighlight#Viewing-highlight-attributes)

```swift
```swift
```swift
```swift
var identifier: any NSCopying & NSSecureCoding
```
```

The unique identifier for the highlight.
```
```swift
```swift
```swift
var url: URL
```
```

The surfaced content URL for the highlight.
```
```

## [Relationships](/documentation/SharedWithYou/SWHighlight#relationships)

### [Inherits From](/documentation/SharedWithYou/SWHighlight#inherits-from)

*   [`NSObject`](/documentation/ObjectiveC/NSObject-swift.class)

### [Inherited By](/documentation/SharedWithYou/SWHighlight#inherited-by)

*   [`SWCollaborationHighlight`](/documentation/sharedwithyou/swcollaborationhighlight)

### [Conforms To](/documentation/SharedWithYou/SWHighlight#conforms-to)

*   [`CVarArg`](/documentation/Swift/CVarArg)
*   [`CustomDebugStringConvertible`](/documentation/Swift/CustomDebugStringConvertible)
*   [`CustomStringConvertible`](/documentation/Swift/CustomStringConvertible)
*   [`Equatable`](/documentation/Swift/Equatable)
*   [`Hashable`](/documentation/Swift/Hashable)
*   [`NSCoding`](/documentation/Foundation/NSCoding)
*   [`NSCopying`](/documentation/Foundation/NSCopying)
*   [`NSObjectProtocol`](/documentation/ObjectiveC/NSObjectProtocol)
*   [`NSSecureCoding`](/documentation/Foundation/NSSecureCoding)

## [See Also](/documentation/SharedWithYou/SWHighlight#see-also)

### [Highlights](/documentation/SharedWithYou/SWHighlight#Highlights)

```swift
```swift
```swift
```swift
class SWHighlightCenter
```
```

An object that contains a priority-ordered list of universal links to share with the current user.
```
```