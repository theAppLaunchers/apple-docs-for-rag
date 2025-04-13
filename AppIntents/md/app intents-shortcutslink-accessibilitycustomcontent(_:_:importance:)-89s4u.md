

- App Intents
- ShortcutsLink
-  accessibilityCustomContent(\_:\_:importance:) 

Instance Method

# accessibilityCustomContent(\_:\_:importance:)

Add additional accessibility information to the view.

AppIntentsSwiftUIiOS 15.0+iPadOS 15.0+Mac Catalyst 15.0+macOS 12.0+tvOS 15.0+visionOS 1.0+watchOS 8.0+

``` source
nonisolated
func accessibilityCustomContent(
    _ key: AccessibilityCustomContentKey,
    _ valueKey: LocalizedStringKey,
    importance: AXCustomContent.Importance = .default
) -> ModifiedContent
```

## Parameters 

`key`  

Key used to specify the identifier and label of the of the additional accessibility information entry.

`valueKey`  

Text value for the additional accessibility information. For example: “landscape.” A value of `nil` will remove any entry of additional information added earlier for any `key` with the same identifier.

`importance`  

Importance of the accessibility information. High-importance information gets read out immediately, while default-importance information must be explicitly asked for by the user.

## Discussion

Use this method to add information you want accessibility users to be able to access about this element, beyond the basics of label, value, and hint. For example, `accessibilityCustomContent` can be used to add information about the orientation of a photograph, or the number of people found in the picture.

Note

Repeated calls of `accessibilityCustomContent` with `key`s having different identifiers will create new entries of additional information. Calling `accessibilityAdditionalContent` repeatedly with `key`s having matching identifiers will replace the previous entry.

