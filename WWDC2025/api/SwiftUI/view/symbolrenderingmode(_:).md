*   [SwiftUI](/documentation/swiftui)
*   [View](/documentation/swiftui/view)
*   symbolRenderingMode(\_:)

Instance Method

# symbolRenderingMode(\_:)

Sets the rendering mode for symbol images within this view.

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
func symbolRenderingMode(_ mode: [`SymbolRenderingMode`](/documentation/swiftui/symbolrenderingmode)?) -> some [`View`](/documentation/swiftui/view)
```

```
```
```
```
```
```
```

## [Parameters](/documentation/SwiftUI/View/symbolRenderingMode\(_:\)#parameters)

`mode`

The symbol rendering mode to use.

## [Return Value](/documentation/SwiftUI/View/symbolRenderingMode\(_:\)#return-value)

A view that uses the rendering mode you supply.

## [See Also](/documentation/SwiftUI/View/symbolRenderingMode\(_:\)#see-also)

### [Setting symbol rendering modes](/documentation/SwiftUI/View/symbolRenderingMode\(_:\)#Setting-symbol-rendering-modes)

```swift
```swift
```swift
```swift
var symbolRenderingMode: SymbolRenderingMode?
```
```

The current symbol rendering mode, or `nil` denoting that the mode is picked automatically using the current image and foreground style as parameters.
```
```swift
```swift
```swift
struct SymbolRenderingMode
```
```

A symbol rendering mode.
```
```swift
```swift
```swift
struct SymbolColorRenderingMode
```
```

A method of filling a layer in a symbol image.

Beta
```
```swift
```swift
```swift
struct SymbolVariableValueMode
```
```

A method of rendering the variable value of a symbol image.

Beta
```
```