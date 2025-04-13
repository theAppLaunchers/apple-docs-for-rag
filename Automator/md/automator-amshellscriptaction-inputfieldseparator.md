

- Automator
- AMShellScriptAction
-  inputFieldSeparator 

Instance Property

# inputFieldSeparator

A string to use as the delimiter between items in the string passed to the action through standard input.

Mac Catalyst 14.0+macOS 10.4+

``` source
var inputFieldSeparator: String { get }
```

## Discussion

The Automator framework converts the output from the previous action (which is usually in the form of a list or array) into a single string in which the array elements are concatenated by the input field separator. By default, this separator is the newline character (`\n`). You can override this method to, for example, return a null character (`\0`) to provide null-terminated strings for `xargs -0`.

## See Also

### Handling the I/O Separator Character

var outputFieldSeparator: String

A string to use as a delimiter in the string output by the action.

var remapLineEndings: Bool

A Boolean value that indicates whether you want automatic remapping of carriage return (`\r`) to newline (`\n`) characters in the input string.

