

- SwiftUI
- View
-  autocorrectionDisabled(\_:) 

Instance Method

# autocorrectionDisabled(\_:)

Sets whether to disable autocorrection for this view.

iOS 13.0+iPadOS 13.0+Mac Catalyst 13.0+macOS 10.15+tvOS 13.0+visionOS 1.0+watchOS 8.0+

``` source
nonisolated
func autocorrectionDisabled(_ disable: Bool = true) -> some View
```

## Parameters 

`disable`  

A Boolean value that indicates whether autocorrection is disabled for this view. The default value is `true`.

## Discussion

Use this method when the effect of autocorrection would make it more difficult for the user to input information. The entry of proper names and street addresses are examples where autocorrection can negatively affect the user’s ability complete a data entry task.

The example below configures a TextField with the default keyboard. Disabling autocorrection allows the user to enter arbitrary text without the autocorrection system offering suggestions or attempting to override their input.

```
TextField("1234 Main St.", text: $address)
    .keyboardType(.default)
    .autocorrectionDisabled(true)
```

## See Also

### Managing text entry

var autocorrectionDisabled: Bool

A Boolean value that determines whether the view hierarchy has auto-correction enabled.

func keyboardType(UIKeyboardType) -> some View

Sets the keyboard type for this view.

func scrollDismissesKeyboard(ScrollDismissesKeyboardMode) -> some View

Configures the behavior in which scrollable content interacts with the software keyboard.

func textContentType(_:)

Sets the text content type for this view, which the system uses to offer suggestions while the user enters text on macOS.

func textInputAutocapitalization(TextInputAutocapitalization?) -> some View

Sets how often the shift key in the keyboard is automatically enabled.

struct TextInputAutocapitalization

The kind of autocapitalization behavior applied during text input.

func textInputCompletion(String) -> some View

Associates a fully formed string with the value of this view when used as a text input suggestion

func textInputSuggestions&lt;S>(() -> S) -> some View

Configures the text input suggestions for this view.

func textInputSuggestions&lt;Data, Content>(Data, content: (Data.Element) -> Content) -> some View

Configures the text input suggestions for this view.

func textInputSuggestions&lt;Data, ID, Content>(Data, id: KeyPath&lt;Data.Element, ID>, content: (Data.Element) -> Content) -> some View

Configures the text input suggestions for this view.

func textContentType(WKTextContentType?) -> some View

Sets the text content type for this view, which the system uses to offer suggestions while the user enters text on a watchOS device.

func textContentType(NSTextContentType?) -> some View

Sets the text content type for this view, which the system uses to offer suggestions while the user enters text on macOS.

func textContentType(UITextContentType?) -> some View

Sets the text content type for this view, which the system uses to offer suggestions while the user enters text on an iOS or tvOS device.

