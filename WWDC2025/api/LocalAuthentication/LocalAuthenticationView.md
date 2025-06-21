*   [Local Authentication](/documentation/localauthentication)
*   LocalAuthenticationView

Structure

# LocalAuthenticationView

A SwiftUI view that displays an authentication interface.

LocalAuthenticationSwiftUImacOS 13.0+

```swift
```swift
```swift
```swift
```swift
```swift
```swift

```swift
@[`MainActor`](/documentation/Swift/MainActor) @preconcurrency
struct LocalAuthenticationView<Label> where Label : [`View`](/documentation/SwiftUI/View)
```

```
```
```
```
```
```
```

## [Overview](/documentation/LocalAuthentication/LocalAuthenticationView#overview)

Use a [`LocalAuthenticationView`](/documentation/localauthentication/localauthenticationview) to display a view that prompts users to authenticate with the app. The view visually represents the state of an [`LAPolicy`](/documentation/localauthentication/lapolicy) evaluation from the [Local Authentication](/documentation/localauthentication) framework.

The following shows a [`LocalAuthenticationView`](/documentation/localauthentication/localauthenticationview) in a Mac app with an implicit [`LAContext`](/documentation/localauthentication/lacontext) instance:

```swift
```swift
```swift
```swift
```swift
```swift
var body: some View {
```
```
    LocalAuthenticationView(
        "Continue with Touch ID",
        reason: Text("Access sandcastle competition designs")
    ) { result in
        switch result {
        case .success:
            print("Authorized")
        case .failure(let error):
            print("Authorization failed: \(error)")
        }
    }
    .controlSize(.large)
}
```
```
```
```

If your app’s authorization flow reuses an existing [`LAContext`](/documentation/localauthentication/lacontext), pass it as part of initializing a [`LocalAuthenticationView`](/documentation/localauthentication/localauthenticationview) and call its [`evaluatePolicy(_:localizedReason:reply:)`](/documentation/localauthentication/lacontext/evaluatepolicy\(_:localizedreason:reply:\)) method after the view appears.

## [Topics](/documentation/LocalAuthentication/LocalAuthenticationView#topics)

### [Authenticating with an implicit context](/documentation/LocalAuthentication/LocalAuthenticationView#Authenticating-with-an-implicit-context)

[`init(reason: Text, context: LAContext?, result: (Result<Void, any Error>) -> Void, label: () -> Label)`](/documentation/localauthentication/localauthenticationview/init\(reason:context:result:label:\))

Creates a local authentication view.

[`init<S>(S, reason: Text, context: LAContext?, result: (Result<Void, any Error>) -> Void)`](/documentation/localauthentication/localauthenticationview/init\(_:reason:context:result:\)-8ubaq)

Creates a local authentication view with a title.

[`init(LocalizedStringKey, reason: Text, context: LAContext?, result: (Result<Void, any Error>) -> Void)`](/documentation/localauthentication/localauthenticationview/init\(_:reason:context:result:\)-917ds)

Creates a local authentication view with a localizable title.

[`init(Text, reason: Text, context: LAContext?, result: (Result<Void, any Error>) -> Void)`](/documentation/localauthentication/localauthenticationview/init\(_:reason:context:result:\)-4pkpi)

Creates a local authentication view with a title text view.

### [Authenticating with a context you supply](/documentation/LocalAuthentication/LocalAuthenticationView#Authenticating-with-a-context-you-supply)

[`init<S>(S, context: LAContext)`](/documentation/localauthentication/localauthenticationview/init\(_:context:\)-9xeoo)

Creates a local authentication view with a required context.

[`init(context: LAContext, label: () -> Label)`](/documentation/localauthentication/localauthenticationview/init\(context:label:\))

Creates a local authentication view with a label and required context.

[`init(LocalizedStringKey, context: LAContext)`](/documentation/localauthentication/localauthenticationview/init\(_:context:\)-676qx)

Creates a local authentication view with a localizable title and required context.

### [Initializers](/documentation/LocalAuthentication/LocalAuthenticationView#Initializers)

[`init(LocalizedStringResource, context: LAContext)`](/documentation/localauthentication/localauthenticationview/init\(_:context:\)-7ejbu)

Creates a new view and pairs it with the specified authentication context.

Beta

[`init(LocalizedStringResource, reason: Text, context: LAContext?, result: (Result<Void, any Error>) -> Void)`](/documentation/localauthentication/localauthenticationview/init\(_:reason:context:result:\)-88u6u)

Creates a new `LocalAuthenticationView`.

## [Relationships](/documentation/LocalAuthentication/LocalAuthenticationView#relationships)

### [Conforms To](/documentation/LocalAuthentication/LocalAuthenticationView#conforms-to)

*   [`Sendable`](/documentation/Swift/Sendable)
*   [`SendableMetatype`](/documentation/Swift/SendableMetatype)
*   [`View`](/documentation/SwiftUI/View)