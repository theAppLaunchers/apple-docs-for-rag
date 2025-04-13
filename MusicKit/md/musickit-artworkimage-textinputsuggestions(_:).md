

- MusicKit
- ArtworkImage
-  textInputSuggestions(\_:) 

Instance Method

# textInputSuggestions(\_:)

Configures the text input suggestions for this view.

MusicKitSwiftUImacOS 15.0+

``` source
nonisolated
func textInputSuggestions(@ViewBuilder _ suggestions: () -> S) -> some View where S : View
```

## Parameters 

`suggestions`  

A view builder that produces content that populates a list of suggestions.

## Discussion

You can suggest text completions during a text input operation by providing a collection of view to this modifier. The interface presents the suggestion views as a list of choices when someone activates the text editing interface.

Associate a string with each suggestion view by adding the `View/textInputCompletion(_:)` modifier to the view.

Use `Label` to get platform-standard visual representations of suggestion text accompanied with images, and `Section` for labelled sections of results.

For example, you can suggest addresses by displaying the venue name, and provide the corresponding address as a text completion in each case:

```
TextField("Location", text: $addressText)
    .textInputSuggestions {
        Text("The Fillmore")
            .textInputCompletion("1805 Geary Blvd, San Francisco")
        Text("The Catalyst")
            .textInputCompletion("1011 Pacific Ave, Santa Cruz")
        Text("Rio Theatre")
            .textInputCompletion("1205 Soquel Ave, Santa Cruz")
    }
```

When someone chooses a suggestion, SwiftUI replaces the text in the text field with the text completion string. If you omit the text completion modifier for a particular suggestion view, SwiftUI displays the suggestion, but the suggestion view doesn’t react to taps or clicks.

You can update the suggestions that you provide as conditions change.

For example, you can specify an array of suggestions that you store in a model:

```
TextField("Location", text: $addressText)
    .textInputSuggestions {
        ForEach(model.suggestedVenues) { venue in
            Label(venue.name, image: venue.image)
                .textInputCompletion(venue.address)
        }
    }
```

If the model’s `suggestedVenues` begins as an empty array, the interface doesn’t display any suggestions to start. You can then provide logic that updates the array based on some condition. For example, you might update the completions based on the current text. Note that certain events or actions, like when someone moves a macOS window, might dismiss the suggestion view.

