

- RealityKit
- RealityViewContent
- RealityViewContent.Body
-  searchDictationBehavior(\_:) 

Instance Method

# searchDictationBehavior(\_:)

Configures the dictation behavior for any search fields configured by the searchable modifier.

RealityKitSwiftUIiOS 17.0+iPadOS 17.0+visionOS 1.0+

``` source
nonisolated
func searchDictationBehavior(_ dictationBehavior: TextInputDictationBehavior) -> some View
```

## Discussion

By default, search fields on visionOS will automatically start dictation when looking at the dictation button in the search field. You can change this behavior by providing a value of `TextInputDictationBehavior/preventDictation` to this modifier.

See the `TextInputDictationBehavior` type for more information on the available dictation behaviors.

