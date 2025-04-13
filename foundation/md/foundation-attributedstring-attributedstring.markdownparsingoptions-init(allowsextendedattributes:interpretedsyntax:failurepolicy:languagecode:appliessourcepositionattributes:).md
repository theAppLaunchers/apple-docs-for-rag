

- Foundation
- AttributedString
- AttributedString.MarkdownParsingOptions
-  init(allowsExtendedAttributes:interpretedSyntax:failurePolicy:languageCode:appliesSourcePositionAttributes:) 

Initializer

# init(allowsExtendedAttributes:interpretedSyntax:failurePolicy:languageCode:appliesSourcePositionAttributes:)

Creates a Markdown parsing options instance with the specified values, optionally marking the source position of attributed text.

iOS 16.0+iPadOS 16.0+Mac Catalyst 16.0+macOS 13.0+tvOS 16.0+visionOS 1.0+watchOS 9.0+

``` source
init(
    allowsExtendedAttributes: Bool = false,
    interpretedSyntax: AttributedString.MarkdownParsingOptions.InterpretedSyntax = .full,
    failurePolicy: AttributedString.MarkdownParsingOptions.FailurePolicy = .throwError,
    languageCode: String? = nil,
    appliesSourcePositionAttributes: Bool = false
)
```

## Parameters 

`allowsExtendedAttributes`  

A Boolean value that indicates whether parsing allows extensions to Markdown that specify extended attributes.

`interpretedSyntax`  

The syntax for intepreting a Markdown string.

`failurePolicy`  

The policy for handling a parsing failure.

`languageCode`  

The BCP-47 language code for this document.

`appliesSourcePositionAttributes`  

A Boolean value that indicates whether parsing applies attributes that indicate the position of attribute text in the original Markdown string. If this value is `true`, the resulting string may contain attributes of type AttributeScopes.FoundationAttributes.MarkdownSourcePositionAttribute.

## See Also

### Creating Markdown Parsing Options

init(allowsExtendedAttributes: Bool, interpretedSyntax: AttributedString.MarkdownParsingOptions.InterpretedSyntax, failurePolicy: AttributedString.MarkdownParsingOptions.FailurePolicy, languageCode: String?)

Creates a Markdown parsing options instance with the specified values.

