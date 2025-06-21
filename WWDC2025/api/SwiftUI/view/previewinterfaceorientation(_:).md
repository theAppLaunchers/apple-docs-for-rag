*   [SwiftUI](/documentation/swiftui)
*   [View](/documentation/swiftui/view)
*   previewInterfaceOrientation(\_:)

Instance Method

# previewInterfaceOrientation(\_:)

Overrides the orientation of the preview.

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
func previewInterfaceOrientation(_ value: [`InterfaceOrientation`](/documentation/swiftui/interfaceorientation)) -> some [`View`](/documentation/swiftui/view)
```

```
```
```
```
```
```
```

## [Parameters](/documentation/SwiftUI/View/previewInterfaceOrientation\(_:\)#parameters)

`value`

An orientation to use for preview.

## [Return Value](/documentation/SwiftUI/View/previewInterfaceOrientation\(_:\)#return-value)

A preview that uses the given orientation.

## [Discussion](/documentation/SwiftUI/View/previewInterfaceOrientation\(_:\)#discussion)

By default, device previews appear right side up, using orientation [`portrait`](/documentation/swiftui/interfaceorientation/portrait). You can change the orientation of a preview using one of the values in the [`InterfaceOrientation`](/documentation/swiftui/interfaceorientation) structure:

```swift
```swift
```swift
```swift
```swift
```swift
struct CircleImage_Previews: PreviewProvider {
```
```
    static var previews: some View {
        CircleImage()
            .previewInterfaceOrientation(.landscapeRight)
    }
}
```
```
```
```

## [See Also](/documentation/SwiftUI/View/previewInterfaceOrientation\(_:\)#see-also)

### [Customizing a preview](/documentation/SwiftUI/View/previewInterfaceOrientation\(_:\)#Customizing-a-preview)

```swift
```swift
```swift
```swift
func previewDevice(PreviewDevice?) -> some View
```
```

Overrides the device for a preview.
```
```swift
```swift
```swift
struct PreviewDevice
```
```

A simulator device that runs a preview.
```
```swift
```swift
```swift
func previewLayout(PreviewLayout) -> some View
```
```

Overrides the size of the container for the preview.
```
```swift
```swift
```swift
struct InterfaceOrientation
```
```

The orientation of the interface from the user’s perspective.
```
```