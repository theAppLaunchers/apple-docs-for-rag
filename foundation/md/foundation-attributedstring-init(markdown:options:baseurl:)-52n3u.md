

- Foundation
- AttributedString
-  init(markdown:options:baseURL:) 

Initializer

# init(markdown:options:baseURL:)

Creates an attributed string from a Markdown-formatted string using the provided options.

iOS 15.0+iPadOS 15.0+Mac Catalyst 15.0+macOS 12.0+tvOS 15.0+visionOS 1.0+watchOS 8.0+

``` source
init(
    markdown: String,
    options: AttributedString.MarkdownParsingOptions = .init(),
    baseURL: URL? = nil
) throws
```

## Parameters 

`markdown`  

The string that contains the Markdown formatting.

`options`  

Options that affect how the initializer interprets formatting in the Markdown string. This parameter defaults to no options.

`baseURL`  

The base URL to use when resolving Markdown URLs. The initializer treats URLs as being relative to this URL. If this value is `nil`, the initializer doesn’t resolve URLs. The default is `nil`.

## Discussion

If your source string includes custom attributes defined by conformers to MarkdownDecodableAttributedStringKey and used with Apple’s markdown extension syntax, be sure to include the allowsExtendedAttributes option. Otherwise, the initializer doesn’t parse these attributes.

## See Also

### Initializing from Markdown Strings

init&lt;S>(markdown: String, including: S.Type, options: AttributedString.MarkdownParsingOptions, baseURL: URL?) throws

Creates an attributed string from a Markdown-formatted string using the provided options and attribute scope.

init&lt;S>(markdown: String, including: KeyPath&lt;AttributeScopes, S.Type>, options: AttributedString.MarkdownParsingOptions, baseURL: URL?) throws

Creates an attributed string from a Markdown-formatted string using the provided options and attribute scope that a key path identifies.

