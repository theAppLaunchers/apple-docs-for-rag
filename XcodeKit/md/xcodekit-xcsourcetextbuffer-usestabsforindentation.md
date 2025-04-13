

- XcodeKit
- XCSourceTextBuffer
-  usesTabsForIndentation 

Instance Property

# usesTabsForIndentation

A Boolean value that indicates whether tabs are used for indentation.

macOS 10.12+

``` source
var usesTabsForIndentation: Bool { get }
```

## Discussion

The `usesTabsForIndentation` property determines whether tab characters are used to indent text instead of space characters when possible. When the indentation width isn’t a multiple of the tab width, space characters are used to pad the indentation to the appropriate width.

For example, consider an `XCSourceTextBuffer` instance that has a tab width of eight, an indentation width of four, and the `usesTabsForIndentation` property set to `true`. The first indentation level is represented by four space characters, the second by a tab character, the third by a tab followed by four space characters, the fourth by two tab characters, and so on.

## See Also

### Configuring Source Editor Indentation

var indentationWidth: Int

The number of space characters used for indentation of the text in the buffer.

var tabWidth: Int

The number of space characters represented by a tab character in the buffer.

