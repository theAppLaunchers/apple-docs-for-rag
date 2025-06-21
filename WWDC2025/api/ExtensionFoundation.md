Framework

# ExtensionFoundation

Create executable bundles to extend the functionality of other apps.

iOS 16.0+iPadOS 16.0+Mac Catalyst 16.0+macOS 13.0+tvOS 17.4+visionOS 1.1+watchOS 9.0+

## [Overview](/documentation/ExtensionFoundation#overview)

Extensions are executable code bundles, in one app that perform functions in a second, _host_ app. Host apps declare _extension points_ that control the kinds of functionality its extensions can implement. Extensions allow iOS and Mac apps to include code that runs inside system apps. For example, [Messages](/documentation/Messages) provides extension points so apps can create `iMessage apps`. Messages automatically finds extension bundles that target its extension points and makes them available in its app drawer. A Mac app can also declare its own extension points so that other apps can extend the Mac app’s functionality.

Prior to macOS 13, apps use [`NSExtension`](/documentation/BundleResources/Information-Property-List/NSExtension) property lists to declare and configure extensions. ExtensionKit supports this approach, but also adds the ability to configure extensions and extension points entirely in Swift code.

Extensions come in two basic forms: UI and non-UI.

UI extensions

Vend remote views and view controllers that the host app adds to its own view hierarchy.

Non-UI extensions

Present no user interface, but perform some work on behalf of the host app.

An iMessage app, which can include sophisticated user interfaces — even entire games — is an example of a UI extension. [SiriKit](/documentation/SiriKit) app intents, which gives people the ability to interact with your app using Siri, is an example of a non-UI extension.

Use ExtensionFoundation by itself to create extensions and extension points that don’t present a user interface. Use ExtensionFoundation in combination with [ExtensionKit](/documentation/ExtensionKit) to create extensions that vend remote view controllers to the host app.

## [Topics](/documentation/ExtensionFoundation#topics)

### [App Extensions](/documentation/ExtensionFoundation#App-Extensions)

```swift
```swift
```swift
```swift
struct AppExtensionIdentity
```
```

An object that uniquely identifies an app extension.
```
```swift
```swift
```swift
protocol AppExtension
```
```

Declares a type used by app extensions.
```
```swift
```swift
```swift
protocol AppExtensionConfiguration
```
```

An object that holds configuration options for an app extension.
```
```

### [Host Apps](/documentation/ExtensionFoundation#Host-Apps)

```swift
```swift
```swift
```swift
struct AppExtensionProcess
```
```

An object that represents a running app extension process.
```
```

### [Protocols](/documentation/ExtensionFoundation#Protocols)

```swift
```swift
```swift
```swift
protocol ExtensionPointDefining
```
```
```
```

### [Structures](/documentation/ExtensionFoundation#Structures)

```swift
```swift
```swift
```swift
struct AppExtensionPoint
```
```

A type representing an extension point
```
```swift
```swift
```swift
struct ConnectionHandler
```
```

ConnectionHandler handles incoming XPC connections.
```
```

### [Type Aliases](/documentation/ExtensionFoundation#Type-Aliases)

```swift
```swift
```swift
```swift
typealias MainFunction
```
```
```
```