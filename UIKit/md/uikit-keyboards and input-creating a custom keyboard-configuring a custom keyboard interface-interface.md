

- UIKit
- Keyboards and input
- Creating a custom keyboard
-  Configuring a custom keyboard interface 

Article

# Configuring a custom keyboard interface

Design a flexible, functional, and responsive interface for editing text.

## Overview

You can create a custom keyboard to provide a systemwide interface for manipulating text input. Because you’ll be integrating your keyboard with a system-provided service, you must fulfill certain requirements, and meet common user expectations.

Among other things, your keyboard must:

- Handle different types of input, like email addresses, phone numbers, URLs, and more.

- Adapt to the space that’s available. For example, iPadOS can display keyboard docked to the bottom of the screen or floating with a compact width.

- Enable users to switch to other keyboards.

### Support different input types

Use the textDocumentProxy to determine the current text input view’s keyboard input type. For each keyboard type that your app supports, configure your interface accordingly. One way to do this is by implementing textWillChange(_:) in your view controller, then compare the textDocumentProxy‘s keyboardType to your keyboard’s current display. If it’s different, update your interface accordingly.

```
let keyboardType = textDocumentProxy.keyboardType

switch(keyboardType) {
case .asciiCapable: …
case .emailAddress: …
case .numberPad: …
…
}
```

Some text input views don’t allow custom keyboards:

- Secure text field entries always show the system keyboard when the user begins entering text in a secure text field, temporarily removing your custom keyboard if it’s active. The system shows your keyboard again when the user begins entering text into a non-secure text field.

- Text input fields configured with a keyboard type of UIKeyboardType.phonePad or UIKeyboardType.namePhonePad show the system keyboard.

An app can disallow the use of third-party keyboards entirely by implementing application(_:shouldAllowExtensionPointIdentifier:) and returning false when called with the `com.apple.keyboard-service` identifier. If an app disallows third-party keyboards, your keyboard won’t be shown in that app.

### Adapt to different layouts

By default, iOS sizes custom keyboards to match the system keyboard according to screen size and device orientation. A custom keyboard’s width is always set by the system, typically matching the screen width. You can adjust the height of your custom keyboard’s primary view using Auto Layout. To change a keyboard’s height, adjust the height constraints on the UIInputViewController’s view to achieve the desired height for your interface.

For more information about laying out your view, see View layout.

### Handle common keyboard behaviors

Users expect various behaviors from keyboards. One example is autocapitalization: In a standard text field, the first letter of a sentence in a case-sensitive language is automatically capitalized.

Features that users commonly expect from any keyboard include:

- Appropriate layout and features based on keyboard type trait, such as automatically displaying relevant keys when editing email addresses or phone numbers

- Autocorrection and suggestion

- Automatic capitalization

- Automatic period upon double space

- Smart quotes

- Caps lock support

- Multistage input for languages that use ideographic characters and symbols, such as Kanji (Japanese) and Hanzi (Chinese)

UIInputViewController conforms to the UITextInputTraits protocol to give access to a wide variety of properties related to these common behaviors. These properties indicate which settings are currently active for things like autocompletion type, autocapitalization type, enabling the Return key, smart quotes, dashes, and more. See UITextInputTraits for a complete list.

Another common behavior is the ability to dismiss the keyboard. Users can end editing in the current text input view by dismissing the keyboard. You can implement a button to dismiss the keyboard by calling dismissKeyboard():

```
@IBAction func dismissButtonTapped(_ sender: Any) {
    dismissKeyboard()
}
```

Custom keyboards also have to provide a way for users to switch keyboards. For more information on implementing a button to switch keyboards, see Add your custom user interface.

### Support autocomplete

To support autocomplete functionality your keyboard has access to UILexicon. Make use of this class, along with a lexicon of your own design, to provide suggestions and autocorrections as users are entering text. The UILexicon object contains words from various sources, including:

- Unpaired first names and last names from the user’s Contacts database.

- Text shortcuts defined in the Settings \> General \> Keyboard \> Shortcuts list.

- A dictionary of common words.

### Indicate dictation support

If your keyboard provides a way to input text using dictation, set the hasDictationKey property of your UIInputViewController’s subclass to true. In some cases, iOS may automatically show a dictation button (for example, on iPhone devices with Face ID). When you set hasDictationKey to true, iOS won’t show the system button, because having two buttons to perform dictation would be confusing to users.

### Leverage your containing app

When designing your custom keyboard, keep in mind that you can leverage your containing app for some functionality. For example, a tutorial would be best suited in your parent app. You could also configure settings or options in the containing app, then save those settings to a shared group container which your keyboard could then read. If your containing app’s sole purpose is to deliver your custom keyboard, there must be some utility provided even if it’s purely informational.

For further design guidance, see Human Interface Guidelines.

## See Also

### Keyboard configuration

Configuring open access for a custom keyboard

Enable network access and write access to a shared group container.

