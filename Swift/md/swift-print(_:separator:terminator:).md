

- Swift
-  print(\_:separator:terminator:) 

Function

# print(\_:separator:terminator:)

Writes the textual representations of the given items into the standard output.

iOS 8.0+iPadOS 8.0+Mac Catalyst 13.0+macOS 10.10+tvOS 9.0+visionOS 1.0+watchOS 2.0+

``` source
func print(
    _ items: Any...,
    separator: String = " ",
    terminator: String = "\n"
)
```

## Parameters 

`items`  

Zero or more items to print.

`separator`  

A string to print between each item. The default is a single space (`" "`).

`terminator`  

The string to print after all items have been printed. The default is a newline (`"\n"`).

## Discussion

You can pass zero or more items to the `print(_:separator:terminator:)` function. The textual representation for each item is the same as that obtained by calling `String(describing: item)`. The following example prints a string, a closed range of integers, and a group of floating-point values to standard output:

```
print("One two three four five")
// Prints "One two three four five"

print(1...5)
// Prints "1...5"

print(1.0, 2.0, 3.0, 4.0, 5.0)
// Prints "1.0 2.0 3.0 4.0 5.0"
```

To print the items separated by something other than a space, pass a string as `separator`.

```
print(1.0, 2.0, 3.0, 4.0, 5.0, separator: " ... ")
// Prints "1.0 ... 2.0 ... 3.0 ... 4.0 ... 5.0"
```

The output from each call to `print(_:separator:terminator:)` includes a newline by default. To print the items without a trailing newline, pass an empty string as `terminator`.

```
for n in 1...5 {
    print(n, terminator: "")
}
// Prints "12345"
```

## See Also

### Printing and Dumping

func print&lt;Target>(Any..., separator: String, terminator: String, to: inout Target)

Writes the textual representations of the given items into the given output stream.

func debugPrint(Any..., separator: String, terminator: String)

Writes the textual representations of the given items most suitable for debugging into the standard output.

func debugPrint&lt;Target>(Any..., separator: String, terminator: String, to: inout Target)

Writes the textual representations of the given items most suitable for debugging into the given output stream.

func dump&lt;T>(T, name: String?, indent: Int, maxDepth: Int, maxItems: Int) -> T

Dumps the given object’s contents using its mirror to standard output.

func dump&lt;T, TargetStream>(T, to: inout TargetStream, name: String?, indent: Int, maxDepth: Int, maxItems: Int) -> T

Dumps the given object’s contents using its mirror to the specified output stream.

