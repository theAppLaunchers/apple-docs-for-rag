*   [UIKit](/documentation/uikit)
*   [UIScene](/documentation/uikit/uiscene)
*   subtitle

Instance Property

# subtitle

A string that the app displays in the title bar of a window when running in macOS.

iOS 15.0+iPadOS 15.0+Mac Catalyst 15.0+tvOS 15.0+visionOS 1.0+

```swift
```swift
```swift
```swift
```swift
```swift
```swift

```swift
@[`MainActor`](/documentation/Swift/MainActor)
var subtitle: [`String`](/documentation/Swift/String) { get set }
```

```
```
```
```
```
```
```

## [Discussion](/documentation/UIKit/UIScene/subtitle#Discussion)

When this property is an empty string, the system removes the subtitle from the window layout. The default value is an empty string.

Note

Apps running in iOS ignore the [`subtitle`](/documentation/uikit/uiscene/subtitle) property.

## [See Also](/documentation/UIKit/UIScene/subtitle#see-also)

### [Getting the scene attributes](/documentation/UIKit/UIScene/subtitle#Getting-the-scene-attributes)

```swift
```swift
```swift
```swift
var activationState: UIScene.ActivationState
```
```

The current execution state of the scene.
```
```swift
```swift
```swift
enum ActivationState
```
```

Constants that indicate the foreground or background execution state of your app.
```
```swift
```swift
```swift
var title: String!
```
```

A user-visible string you supply to help users differentiate among your app’s scenes.
```
```