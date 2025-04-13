

- App Intents
- ShortcutsLink
-  textInputAutocapitalization(\_:) 

Instance Method

# textInputAutocapitalization(\_:)

Sets how often the shift key in the keyboard is automatically enabled.

AppIntentsSwiftUIiOS 15.0+iPadOS 15.0+Mac Catalyst 15.0+tvOS 15.0+visionOS 1.0+watchOS 8.0+

``` source
nonisolated
func textInputAutocapitalization(_ autocapitalization: TextInputAutocapitalization?) -> some View
```

## Parameters 

`autocapitalization`  

One of the capitalizing behaviors defined in the `TextInputAutocapitalization` struct or nil.

## Discussion

Use `textInputAutocapitalization(_:)` when you need to automatically capitalize words, sentences, or other text like proper nouns.

In example below, as the user enters text the shift key is automatically enabled before every word:

```
TextField("Last, First", text: $fullName)
    .textInputAutocapitalization(.words)
```

The `TextInputAutocapitalization` struct defines the available autocapitalizing behavior. Providing `nil` to this view modifier does not change the autocapitalization behavior. The default is `TextInputAutocapitalization.sentences`.

