

- Foundation
- NSRegularExpression
-  replacementString(for:in:offset:template:) 

Instance Method

# replacementString(for:in:offset:template:)

Used to perform template substitution for a single result for clients implementing their own replace functionality.

iOS 2.0+iPadOS 2.0+Mac Catalyst 13.0+macOS 10.0+tvOS 9.0+visionOS 1.0+watchOS 2.0+

``` source
func replacementString(
    for result: NSTextCheckingResult,
    in string: String,
    offset: Int,
    template templ: String
) -> String
```

## Parameters 

`result`  

The result of the single match.

`string`  

The string from which the result was matched.

`offset`  

The offset to be added to the location of the result in the string.

`templ`  

See Flag Options for the format of `template`.

## Return Value

A replacement string.

## Discussion

For clients implementing their own replace functionality, this is a method to perform the template substitution for a single result, given the string from which the result was matched, an offset to be added to the location of the result in the string (for example, in cases that modifications to the string moved the result since it was matched), and a replacement template.

This is an advanced method that is used only if you wanted to iterate through a list of matches yourself and do the template replacement for each one, plus maybe some other calculation that you want to do in code, then you would use this at each step.

