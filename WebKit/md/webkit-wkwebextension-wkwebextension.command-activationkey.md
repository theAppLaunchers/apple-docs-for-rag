

- WebKit
- WKWebExtension
- WKWebExtension.Command
-  activationKey 

Instance Property

# activationKey

The primary key used to trigger the command, distinct from any modifier flags.

iOS 18.4+iPadOS 18.4+Mac Catalyst 18.4+macOS 15.4+visionOS 2.4+

``` source
@MainActor
var activationKey: String? { get set }
```

## Discussion

This property can be customized within the app to avoid conflicts with existing shortcuts or to enable user personalization.

It should accurately represent the activation key as used by the app, which the extension can use to display the complete shortcut in its interface.

If no shortcut is desired for the command, the property should be set to `nil`. This value should be saved and restored as needed by the app.

