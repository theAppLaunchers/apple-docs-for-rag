

- Swift
-  transcode(\_:from:to:stoppingOnError:into:) 

Function

# transcode(\_:from:to:stoppingOnError:into:)

Translates the given input from one Unicode encoding to another by calling the given closure.

iOS 8.0+iPadOS 8.0+Mac Catalyst 13.0+macOS 10.10+tvOS 9.0+visionOS 1.0+watchOS 2.0+

``` source
func transcode(
    _ input: Input,
    from inputEncoding: InputEncoding.Type,
    to outputEncoding: OutputEncoding.Type,
    stoppingOnError stopOnError: Bool,
    into processCodeUnit: (OutputEncoding.CodeUnit) -> Void
) -> Bool where Input : IteratorProtocol, InputEncoding : _UnicodeEncoding, OutputEncoding : _UnicodeEncoding, Input.Element == InputEncoding.CodeUnit
```

## Parameters 

`input`  

An iterator of code units to be translated, encoded as `inputEncoding`. If `stopOnError` is `false`, the entire iterator will be exhausted. Otherwise, iteration will stop if an encoding error is detected.

`inputEncoding`  

The Unicode encoding of `input`.

`outputEncoding`  

The destination Unicode encoding.

`stopOnError`  

Pass `true` to stop translation when an encoding error is detected in `input`. Otherwise, a Unicode replacement character (`"\u{FFFD}"`) is inserted for each detected error.

`processCodeUnit`  

A closure that processes one `outputEncoding` code unit at a time.

## Return Value

`true` if the translation detected encoding errors in `input`; otherwise, `false`.

## Discussion

The following example transcodes the UTF-8 representation of the string `"Fermata 𝄐"` into UTF-32.

```
let fermata = "Fermata 𝄐"
let bytes = fermata.utf8
print(Array(bytes))
// Prints "[70, 101, 114, 109, 97, 116, 97, 32, 240, 157, 132, 144]"

var codeUnits: [UTF32.CodeUnit] = []
let sink = { codeUnits.append($0) }
transcode(bytes.makeIterator(), from: UTF8.self, to: UTF32.self,
          stoppingOnError: false, into: sink)
print(codeUnits)
// Prints "[70, 101, 114, 109, 97, 116, 97, 32, 119056]"
```

The `sink` closure is called with each resulting UTF-32 code unit as the function iterates over its input.

