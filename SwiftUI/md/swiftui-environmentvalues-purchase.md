

- SwiftUI
- EnvironmentValues
-  purchase 

Instance Property

# purchase

An action that starts an in-app purchase.

StoreKitSwiftUIiOS 17.0+iPadOS 17.0+Mac Catalyst 17.0+macOS 14.0+tvOS 17.0+visionOS 1.0+watchOS 10.0+

``` source
var purchase: PurchaseAction { get }
```

## Discussion

Read this environment value to get an `PurchaseAction` instance for a given Environment. Call the instance to start an in-app purchase. You call the instance directly because it defines a `PurchaseAction/callAsFunction(_:options:)` method that Swift calls when you call the instance.

For example, you can start an in-app purchase when the user taps a button:

```
struct PurchaseExample: View {
    @Environment(\.purchase) private var purchase
    let product: Product
    let purchaseOptions: [Product.PurchaseOption]

    var body: some View {
        Button {
            Task {
                let purchaseResult = try? await purchase(product, options: purchaseOptions)
                // Process purchase result.
            }
        } label: {
            Text(product.displayName)
        }
    }
}
```

## See Also

### Actions

var dismiss: DismissAction

An action that dismisses the current presentation.

var dismissSearch: DismissSearchAction

An action that ends the current search interaction.

var dismissWindow: DismissWindowAction

A window dismissal action stored in a view’s environment.

var openImmersiveSpace: OpenImmersiveSpaceAction

An action that presents an immersive space.

var dismissImmersiveSpace: DismissImmersiveSpaceAction

An immersive space dismissal action stored in a view’s environment.

var newDocument: NewDocumentAction

An action in the environment that presents a new document.

var openDocument: OpenDocumentAction

An action in the environment that presents an existing document.

var openURL: OpenURLAction

An action that opens a URL.

var openWindow: OpenWindowAction

A window presentation action stored in a view’s environment.

var pushWindow: PushWindowAction

A window presentation action stored in a view’s environment.

var refresh: RefreshAction?

A refresh action stored in a view’s environment.

var rename: RenameAction?

An action that activates the standard rename interaction.

var resetFocus: ResetFocusAction

An action that requests the focus system to reevaluate default focus.

var openSettings: OpenSettingsAction

A Settings presentation action stored in a view’s environment.

