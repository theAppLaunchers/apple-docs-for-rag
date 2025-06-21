*   [SwiftUI](/documentation/swiftui)
*   [View](/documentation/swiftui/view)
*   symbolVariant(\_:)

Instance Method

# symbolVariant(\_:)

Makes symbols within the view show a particular variant.

iOS 15.0+iPadOS 15.0+Mac Catalyst 15.0+macOS 12.0+tvOS 15.0+visionOS 1.0+watchOS 8.0+

```swift
```swift
```swift
```swift
```swift
```swift
```swift

```swift
nonisolated
func symbolVariant(_ variant: [`SymbolVariants`](/documentation/swiftui/symbolvariants)) -> some [`View`](/documentation/swiftui/view)
```

```
```
```
```
```
```
```

## [Parameters](/documentation/SwiftUI/View/symbolVariant\(_:\)#parameters)

`variant`

The variant to use for symbols. Use the values in [`SymbolVariants`](/documentation/swiftui/symbolvariants).

## [Return Value](/documentation/SwiftUI/View/symbolVariant\(_:\)#return-value)

A view that applies the specified symbol variant or variants to itself and its child views.

## [Discussion](/documentation/SwiftUI/View/symbolVariant\(_:\)#discussion)

When you want all the [SF Symbols](/design/Human-Interface-Guidelines/sf-symbols) in a part of your app’s user interface to use the same variant, use the `symbolVariant(_:)` modifier with a [`SymbolVariants`](/documentation/swiftui/symbolvariants) value, like [`fill`](/documentation/swiftui/symbolvariants/fill-swift.type.property):

```

```
VStack(spacing: 20) {
    HStack(spacing: 20) {
        Image(systemName: "person")
        Image(systemName: "folder")
        Image(systemName: "gearshape")
        Image(systemName: "list.bullet")
    }
    HStack(spacing: 20) {
        Image(systemName: "person")
        Image(systemName: "folder")
        Image(systemName: "gearshape")
        Image(systemName: "list.bullet")
    }
    .symbolVariant(.fill) // Shows filled variants, when available.
}
```

```

A symbol that doesn’t have the specified variant remains unaffected. In the example above, the `list.bullet` symbol doesn’t have a filled variant, so the `symbolVariant(_:)` modifer has no effect.

![A screenshot showing two rows of four symbols. Both rows contain a](https://docs-assets.developer.apple.com/published/101616116d85f2d65120a60c8df2c8c5/View-symbolVariant-1%402x.png)

If you apply the modifier more than once, its effects accumulate. Alternatively, you can apply multiple variants in one call:

```

```
Label("Airplane", systemImage: "airplane.circle.fill")
Label("Airplane", systemImage: "airplane")
    .symbolVariant(.circle)
    .symbolVariant(.fill)
Label("Airplane", systemImage: "airplane")
    .symbolVariant(.circle.fill)
```

```

All of the labels in the code above produce the same output:

![A screenshot of a label that shows an airplane in a filled circle](https://docs-assets.developer.apple.com/published/a5f6c4ed259fb2c02438f67a3dc5e9a1/View-symbolVariant-2%402x.png)

You can apply all these variants in any order, but if you apply more than one shape variant, the one closest to the symbol takes precedence. For example, the following image uses the [`square`](/documentation/swiftui/symbolvariants/square-swift.type.property) shape:

```

```
Image(systemName: "arrow.left")
    .symbolVariant(.square) // This shape takes precedence.
    .symbolVariant(.circle)
    .symbolVariant(.fill)
```

```

![A screenshot of a left arrow symbol in a filled](https://docs-assets.developer.apple.com/published/b522e834c28745be154c9812b0e1971f/View-symbolVariant-3%402x.png)

To cause a symbol to ignore the variants currently in the environment, directly set the [`symbolVariants`](/documentation/swiftui/environmentvalues/symbolvariants) environment value to [`none`](/documentation/swiftui/symbolvariants/none) using the [`environment(_:_:)`](/documentation/swiftui/view/environment\(_:_:\)) modifer.

## [See Also](/documentation/SwiftUI/View/symbolVariant\(_:\)#see-also)

### [Setting a symbol variant](/documentation/SwiftUI/View/symbolVariant\(_:\)#Setting-a-symbol-variant)

```swift
```swift
```swift
```swift
var symbolVariants: SymbolVariants
```
```

The symbol variant to use in this environment.
```
```swift
```swift
```swift
struct SymbolVariants
```
```

A variant of a symbol.
```
```