Framework

# ExtensionKit

Create executable bundles to extend the functionality of other apps by presenting a user interface.

iOS 16.1+iPadOS 16.1+Mac Catalyst 16.0+macOS 13.0+tvOS 16.0+visionOS 1.0+watchOS 10.0+

## [Overview](/documentation/ExtensionKit#overview)

Extensions are executable code bundles, in one app that perform functions in a second, _host_ app. Host apps declare _extension points_ that control the kinds of functionality its extensions can implement. Extensions allow iOS and Mac apps to include code that runs inside system apps. For example, [Messages](/documentation/Messages) provides extension points so apps can create [Messages](/documentation/Messages). Messages automatically finds extension bundles that target its extension points and makes them available in its app drawer. A Mac app can also declare its own extension points so that other apps can extend the Mac app’s functionality.

Prior to macOS 13, apps use [`NSExtension`](/documentation/BundleResources/Information-Property-List/NSExtension) property lists to declare and configure extensions. ExtensionKit supports this approach, but also adds the ability to configure extensions and extension points entirely in Swift code.

Extensions come in two basic forms: UI and non-UI.

UI extensions

Vend remote views and view controllers that the host app adds to its own view hierarchy.

Non-UI extensions

Present no user interface, but perform some work on behalf of the host app.

An iMessage app, which can include sophisticated user interfaces — even entire games — is an example of a UI extension. [SiriKit](/documentation/SiriKit) app intents, which gives people the ability to interact with your app using Siri, is an example of a non-UI extension.

Use ExtensionKit, in combination with [ExtensionFoundation](/documentation/ExtensionFoundation), to create extensions and extension points for UI extensions. To create extensions with no user interface, use [ExtensionFoundation](/documentation/ExtensionFoundation).

## [Topics](/documentation/ExtensionKit#topics)

### [UI App Extensions](/documentation/ExtensionKit#UI-App-Extensions)

```swift
```swift
```swift
```swift
protocol AppExtensionScene
```
```

A protocol that defines the user interface for an application extension.
```
```swift
```swift
```swift
struct AppExtensionSceneConfiguration
```
```

An object that holds configuration options for an extension scene.
```
```swift
```swift
```swift
struct AppExtensionSceneBuilder
```
```

A custom parameter attribute that constructs extension scenes from closures.
```
```swift
```swift
```swift
struct PrimitiveAppExtensionScene
```
```

A primitive you use to compose specialized app extension points.
```
```

### [Host Apps](/documentation/ExtensionKit#Host-Apps)

```swift
```swift
```swift
```swift
class EXHostViewController
```
```

A view controller that hosts remote views provided by an extension.
```
```swift
```swift
```swift
class EXAppExtensionBrowserViewController
```
```

A view controller that allows users to enable and disable extensions.
```
```