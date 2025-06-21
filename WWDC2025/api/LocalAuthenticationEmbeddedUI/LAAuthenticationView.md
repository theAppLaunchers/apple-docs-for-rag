*   [Local Authentication Embedded UI](/documentation/localauthenticationembeddedui)
*   LAAuthenticationView

Class

# LAAuthenticationView

A graphical representation of the state of biometric authentication.

macOS 12.0+

```swift
```swift
```swift
```swift
```swift
```swift
```swift

```swift
@[`MainActor`](/documentation/Swift/MainActor)
class LAAuthenticationView
```

```
```
```
```
```
```
```

## [Overview](/documentation/LocalAuthenticationEmbeddedUI/LAAuthenticationView#overview)

In the view that you use to manage authentication, add a local authentication view as a subview and provide it with an [`LAContext`](/documentation/LocalAuthentication/LAContext) instance. For example, you can do this in the doc://com.apple.documentation/documentation/appkit/nsviewcontroller/1434405-loadview method of your view controller:

```swift
```swift
```swift
```swift
```swift
```swift
func loadView() {
```
```
    laContext = LAContext()
    laView = LAAuthenticationView(context: laContext)
    view.addSubview(laView)
    laView.translatesAutoresizingMaskIntoConstraints = false
    // Add more subviews and layout constraints...
}
```
```
```
```

When the view appears, call the context’s [`evaluatePolicy(_:localizedReason:reply:)`](/documentation/LocalAuthentication/LAContext/evaluatePolicy\(_:localizedReason:reply:\)) method to initiate the authentication:

```swift

```swift
override func viewDidAppear() {
    super.viewDidAppear()
    laContext.evaluatePolicy(
        .deviceOwnerAuthenticationWithBiometricsOrWatch,
        localizedReason: "access your data"
    ) { success, error in
        // Handle the result.
    }
}
```

```

The local authentication view displays an icon that depends on the type of authentication you request, and the types of authentication that the system supports. For example, for a device that supports Touch ID, if you request the [`deviceOwnerAuthenticationWithBiometricsOrWatch`](/documentation/LocalAuthentication/LAPolicy/deviceOwnerAuthenticationWithBiometricsOrWatch) policy, like in the example above, the view displays the familiar finger print icon:

![A screenshot of a circular icon with a pattern that resembles a finger print.](https://docs-assets.developer.apple.com/published/63abc31f750ffd3e74f794a1a8a9e37c/laauthenticationview-1%402x.png)

In the case above, if the user has a connected Apple Watch, that authentication mechanism works as well. If you limit the authentication to the [`deviceOwnerAuthenticationWithWatch`](/documentation/LocalAuthentication/LAPolicy/deviceOwnerAuthenticationWithWatch) policy, the icon shows an Apple Watch in profile:

![A screenshot of a circular icon containing the profile of an Apple Watch.](https://docs-assets.developer.apple.com/published/27733d7dd339bc1a9956c15a7d5f16b7/laauthenticationview-2%402x.png)

You can include other content around this icon that suits your app. The system also displays a message on the Touch Bar or on the user’s Apple Watch, if appropriate. When the evaluation succeeds, the icon transitions into a checkmark:

![A screenshot of a circular icon with a blue checkmark inside.](https://docs-assets.developer.apple.com/published/8172fa3530a97505e520e30b6d4e1845/laauthenticationview-3%402x.png)

If you call the evaluation without first attaching it to a local authentication view, the system shows a standard authentication alert instead.

## [Topics](/documentation/LocalAuthenticationEmbeddedUI/LAAuthenticationView#topics)

### [Creating a local authentication view](/documentation/LocalAuthenticationEmbeddedUI/LAAuthenticationView#Creating-a-local-authentication-view)

[`init(context: LAContext)`](/documentation/localauthenticationembeddedui/laauthenticationview/init\(context:\))

Creates a new authentication icon that reflects the current authentication state.

```swift
```swift
```swift
var context: LAContext
```
```

The local authentication context associated with the authentication view.
```

### [Controlling the size of a local authentication view](/documentation/LocalAuthenticationEmbeddedUI/LAAuthenticationView#Controlling-the-size-of-a-local-authentication-view)

[`init(context: LAContext, controlSize: NSControl.ControlSize)`](/documentation/localauthenticationembeddedui/laauthenticationview/init\(context:controlsize:\))

Creates a new authentication icon that reflects the current authentication state, using a specified size.

```swift
```swift
```swift
var controlSize: NSControl.ControlSize
```
```

The size of the local authentication view user interface element.
```

## [Relationships](/documentation/LocalAuthenticationEmbeddedUI/LAAuthenticationView#relationships)

### [Inherits From](/documentation/LocalAuthenticationEmbeddedUI/LAAuthenticationView#inherits-from)

*   [`NSView`](/documentation/AppKit/NSView)

### [Conforms To](/documentation/LocalAuthenticationEmbeddedUI/LAAuthenticationView#conforms-to)

*   [`CVarArg`](/documentation/Swift/CVarArg)
*   [`CustomDebugStringConvertible`](/documentation/Swift/CustomDebugStringConvertible)
*   [`CustomStringConvertible`](/documentation/Swift/CustomStringConvertible)
*   [`Equatable`](/documentation/Swift/Equatable)
*   [`Hashable`](/documentation/Swift/Hashable)
*   [`NSAccessibilityElementProtocol`](/documentation/AppKit/NSAccessibilityElementProtocol)
*   [`NSAccessibilityProtocol`](/documentation/AppKit/NSAccessibilityProtocol)
*   [`NSAnimatablePropertyContainer`](/documentation/AppKit/NSAnimatablePropertyContainer)
*   [`NSAppearanceCustomization`](/documentation/AppKit/NSAppearanceCustomization)
*   [`NSCoding`](/documentation/Foundation/NSCoding)
*   [`NSDraggingDestination`](/documentation/AppKit/NSDraggingDestination)
*   [`NSObjectProtocol`](/documentation/ObjectiveC/NSObjectProtocol)
*   [`NSStandardKeyBindingResponding`](/documentation/AppKit/NSStandardKeyBindingResponding)
*   [`NSTouchBarProvider`](/documentation/AppKit/NSTouchBarProvider)
*   [`NSUserActivityRestoring`](/documentation/AppKit/NSUserActivityRestoring)
*   [`NSUserInterfaceItemIdentification`](/documentation/AppKit/NSUserInterfaceItemIdentification)