*   [SharedWithYou](/documentation/sharedwithyou)
*   SWHighlightCenterDelegate

Protocol

# SWHighlightCenterDelegate

The protocol you use to notify the delegate when the list or rank order of surfaced highlights changes.

iOSiPadOSMac CatalystmacOStvOSvisionOS

```swift
```swift
```swift
```swift
```swift
```swift
```swift
```swift
protocol SWHighlightCenterDelegate : [`NSObjectProtocol`](/documentation/ObjectiveC/NSObjectProtocol)
```
```
```
```
```
```
```
```

## [Topics](/documentation/SharedWithYou/SWHighlightCenterDelegate#topics)

### [Protocol Attributes](/documentation/SharedWithYou/SWHighlightCenterDelegate#Protocol-Attributes)

```swift
```swift
```swift
```swift
func highlightCenterHighlightsDidChange(SWHighlightCenter)
```
```

Notifies the delegate that the list or rank order of surfaced highlights has changed.

**Required**
```
```

## [Relationships](/documentation/SharedWithYou/SWHighlightCenterDelegate#relationships)

### [Inherits From](/documentation/SharedWithYou/SWHighlightCenterDelegate#inherits-from)

*   [`NSObjectProtocol`](/documentation/ObjectiveC/NSObjectProtocol)

## [See Also](/documentation/SharedWithYou/SWHighlightCenterDelegate#see-also)

### [Setting the delegate](/documentation/SharedWithYou/SWHighlightCenterDelegate#Setting-the-delegate)

```swift
```swift
```swift
```swift
var delegate: (any SWHighlightCenterDelegate)?
```
```

The delegate object for the highlight center.
```
```