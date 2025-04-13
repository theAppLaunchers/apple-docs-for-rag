

- WatchKit
- WKInterfaceController
-  presentTextInputControllerWithSuggestions(forLanguage:allowedInputMode:completion:) 

Instance Method

# presentTextInputControllerWithSuggestions(forLanguage:allowedInputMode:completion:)

Displays a modal interface for gathering language-specific text input from the user.

watchOS 2.0+

``` source
@MainActor
func presentTextInputControllerWithSuggestions(
    forLanguage suggestionsHandler: ((String) -> [Any]?)?,
    allowedInputMode inputMode: WKTextInputMode,
    completion: @escaping ([Any]?) -> Void
)
```

``` source
@MainActor
func presentTextInputControllerWithSuggestions(
    forLanguage suggestionsHandler: ((String) -> [Any]?)?,
    allowedInputMode inputMode: WKTextInputMode
) async -> [Any]?
```

## Parameters 

`suggestionsHandler`  

A block that provides suggestions based on the current language. WatchKit calls this block for the user’s specified language and may call it again if the language changes. The block returns the suggestions to display for the specified language. The block returns an array of NSString objects representing the suggestions and takes the following parameter:

inputLanguage  
The language for which to return suggestions. Use this string to determine what text suggestions to return from the block.

`inputMode`  

The type of input to allow. For a list of possible values, see WKTextInputMode.

`completion`  

The block to execute after the user dismisses the modal interface. This block has no return value and takes the following parameter:

results  
An array containing the input from the user, or `nil` if the user canceled the operation. When an array is provided, the value in the array is usually an NSString object representing the text input. The array can also contain an emoji image, packaged as an NSData object. You can use the data object to create a corresponding UIImage object.

## Discussion

This method executes asynchronously, returning shortly after you call it. During a subsequent run loop cycle, the system calls your `suggestionsHandler` block to retrieve the text suggestions for the user’s current language. Shortly after, it displays a text input controller to the user. The input controller displays the list of input phrases you specify and provides options to enter new text phrases through dictation or to select from a list of emoji. If the user changes the input language, the system calls your `suggestionsHandler` block again to retrieve suggestions for the new language.

When the user accepts a value or cancels input, the text input controller dismisses itself and then executes the block in the `completion` parameter on the WatchKit extension’s main thread. Use the block to retrieve the accepted value and apply it to your content. The presenting interface controller is activated before the block is executed.

Always call this method from your WatchKit extension’s main thread.

## See Also

### Handling text input

func presentTextInputController(withSuggestions: [String]?, allowedInputMode: WKTextInputMode, completion: ([Any]?) -> Void)

Displays a modal interface for gathering text input from the user.

func dismissTextInputController()

Dismisses the text input controller without returning any text.

enum WKTextInputMode

The input modes supported by the text input controller.

