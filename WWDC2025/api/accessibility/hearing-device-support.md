Collection

*   [Accessibility](/documentation/accessibility)
*   [Accessibility API](/documentation/accessibility/accessibility-api)
*   Hearing device support

API Collection

# Hearing device support

Access information about paired hearing aid devices and streaming status.

## [Overview](/documentation/Accessibility/hearing-device-support#overview)

Companion apps for hearing device manufacturers might offer certain features, like remote fitting and hearing device health checks, that rely on streaming audio to the hearing devices. If a user disables audio streaming on their Apple device, these features might become unavailable.

This API gives your app the ability to check the state of the streaming preferences, so you can ask users to temporarily enable streaming to use your app’s features. You can also query other information about streaming capabilities and paired hearing devices.

Use this API to check:

*   The state of the streaming preferences for the hearing device in each ear
    
*   Whether the iOS device supports bidirectional streaming
    
*   The Bluetooth UUIDs of the paired hearing devices that match your app’s `hearing.aid.app` entitlement
    

## [Topics](/documentation/Accessibility/hearing-device-support#topics)

### [Hearing devices](/documentation/Accessibility/hearing-device-support#Hearing-devices)

```swift
```swift
```swift
```swift
struct AXMFiHearingDevice
```
```

A namespace for hearing device accessibility symbols in Swift.
```
```

### [Streaming status](/documentation/Accessibility/hearing-device-support#Streaming-status)

```swift
```swift
```swift
```swift
struct Ear
```
```

Constants that represent a hearing device ear.
```

[`static func streamingEar() -> AXMFiHearingDevice.Ear`](/documentation/accessibility/axmfihearingdevice/streamingear\(\))

Returns which ears enable streaming.

[`static let streamingEarDidChangeNotification: NSNotification.Name`](/documentation/accessibility/axmfihearingdevice/streamingeardidchangenotification)

A notification that the system posts when there’s a change to which ears enable streaming.
```

### [Streaming type](/documentation/Accessibility/hearing-device-support#Streaming-type)

[`static func supportsBidirectionalStreaming() -> Bool`](/documentation/accessibility/axmfihearingdevice/supportsbidirectionalstreaming\(\))

Returns a Boolean value that indicates whether the iOS device supports bidirectional streaming.

### [Paired hearing devices](/documentation/Accessibility/hearing-device-support#Paired-hearing-devices)

[`static func pairedDeviceIdentifiers() -> [UUID]`](/documentation/accessibility/axmfihearingdevice/paireddeviceidentifiers\(\))

Returns the UUIDs of the hearing device peripherals.

[`static let pairedUUIDsDidChangeNotification: NSNotification.Name`](/documentation/accessibility/axmfihearingdevice/paireduuidsdidchangenotification)

A notification that the system posts when there’s a change to the UUIDs of the hearing device peripherals.

## [See Also](/documentation/Accessibility/hearing-device-support#see-also)

### [Features](/documentation/Accessibility/hearing-device-support#Features)

[

API Reference

Customized accessibility content](/documentation/accessibility/customized-accessibility-content)

Customize your apps to deliver accessibility information to your users in measured portions as they need it.

[

API Reference

Audio graphs](/documentation/accessibility/audio-graphs)

Define an accessible representation of your chart for VoiceOver to generate an audio graph.

[

API Reference

Braille displays](/documentation/accessibility/braille-displays)

Display a graphical representation of images, icons, data, and more on a two-dimensional braille display.

```swift
```swift
```swift
func AXNameFromColor(CGColor) -> String
```
```

Returns a localized description of the color to use in accessibility attributes.
```