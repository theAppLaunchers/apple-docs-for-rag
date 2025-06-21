Framework

# CoreLocationUI

Streamline access to users’ location data through a standard, secure UI.

iOS 15.0+iPadOS 15.0+Mac Catalyst 15.0+watchOS 10.0+

## [Overview](/documentation/CoreLocationUI#Overview)

The CoreLocationUI framework contains a standardized UI that interacts securely with [Core Location](/documentation/CoreLocation) to request authorization to access location data.

CoreLocationUI provides [`LocationButton`](/documentation/corelocationui/locationbutton) for SwiftUI apps and [`CLLocationButton`](/documentation/corelocationui/cllocationbutton) for UIKit apps. Add these buttons to your UI when you want someone to grant one-time authorization for your app to fetch their location. The button’s style is consistent with the standard Core Location design language, giving users a sense of familiarity and trust when they interact with it.

Note

The location button ignores user input on Mac apps built with Mac Catalyst, and on compatible iPad and iPhone apps running in visionOS.

## [Topics](/documentation/CoreLocationUI#topics)

### [Location authorization](/documentation/CoreLocationUI#Location-authorization)

[

Sharing Your Location to Find a Park](/documentation/corelocationui/sharing-your-location-to-find-a-park)

Ask for location access using a customizable location button.

```swift
```swift
```swift
struct LocationButton
```
```

A SwiftUI button that grants one-time location authorization.
```
```swift
```swift
```swift
class CLLocationButton
```
```

A button that grants one-time location authorization.
```

### [Button customization](/documentation/CoreLocationUI#Button-customization)

```swift
```swift
```swift
```swift
enum CLLocationButtonIcon
```
```

Constants that specify styles for the location arrow icon on the button.
```
```swift
```swift
```swift
enum CLLocationButtonLabel
```
```

Constants that specify the text of the button label.
```
```