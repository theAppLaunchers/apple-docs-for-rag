*   [SwiftUI](/documentation/swiftui)
*   [Text input and output](/documentation/swiftui/text-input-and-output)
*   Building rich SwiftUI text experiences Beta

Sample Code

# Building rich SwiftUI text experiences

Build an editor for formatted text using SwiftUI text editor views and attributed strings.

[Download](https://docs-assets.developer.apple.com/published/af5124237a05/BuildingRichSwiftUITextExperiences.zip)

iOS 26.0+BetaiPadOS 26.0+BetaXcode 26.0+Beta

## [Overview](/documentation/SwiftUI/building-rich-swiftui-text-experiences#Overview)

Note

This sample code project is associated with WWDC25 session 280: [Code-along: Cook up a rich text experience in SwiftUI with AttributedString](https://developer.apple.com/wwdc25/280/).

You can follow along with the code written in the WWDC25 session, learning how to upgrade `TextEditor` to rich text, build custom controls, and constrain the formatting options the editor provides.

After the code-along, you can learn more about how to persist rich text using SwiftData, and how to export rich text documents using the `Transferable` protocol.

### [Configure the sample code project](/documentation/SwiftUI/building-rich-swiftui-text-experiences#Configure-the-sample-code-project)

To configure the sample code project, do the following in Xcode:

1.  Open the sample with the latest version of Xcode.
    
2.  Set the developer team to let Xcode automatically manage the provisioning profile. For more information, see [Set the bundle ID](/documentation/Xcode/preparing-your-app-for-distribution) and [Assign the project to a team](/documentation/Xcode/preparing-your-app-for-distribution).
    

## [See Also](/documentation/SwiftUI/building-rich-swiftui-text-experiences#see-also)

### [Getting text input](/documentation/SwiftUI/building-rich-swiftui-text-experiences#Getting-text-input)

```swift
```swift
```swift
```swift
struct TextField
```
```

A control that displays an editable text interface.
```
```swift
```swift
```swift
func textFieldStyle<S>(S) -> some View
```
```

Sets the style for text fields within this view.
```
```swift
```swift
```swift
struct SecureField
```
```

A control into which people securely enter private text.
```
```swift
```swift
```swift
struct TextEditor
```
```

A view that can display and edit long-form text.
```
```

Beta Software

This documentation contains preliminary information about an API or technology in development. This information is subject to change, and software implemented according to this documentation should be tested with final operating system software.

[Learn more about using Apple's beta software](https://developer.apple.com/support/beta-software/)