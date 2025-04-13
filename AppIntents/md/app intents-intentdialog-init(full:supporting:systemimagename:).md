

- App Intents
- IntentDialog
-  init(full:supporting:systemImageName:) 

Initializer

# init(full:supporting:systemImageName:)

The text you want the system to display, or speak, when requesting a value, asking for disambiguation, or confirming an action.

iOS 17.2+iPadOS 17.2+Mac Catalyst 17.2+macOS 14.2+tvOS 17.2+visionOS 1.0+watchOS 10.2+

``` source
init(
    full: LocalizedStringResource,
    supporting: LocalizedStringResource,
    systemImageName: String
)
```

## Discussion

Parameters:

- full: a standalone message that fully describes the output

- supporting: a message that may be used in conjunction with visual output

- systemImageName: an SF Symbol that may be be used to represent the result

