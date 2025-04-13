

- Swift
- Unicode
- Unicode.UTF16
-  transcodedLength(of:decodedAs:repairingIllFormedSequences:) 

Type Method

# transcodedLength(of:decodedAs:repairingIllFormedSequences:)

Returns the number of UTF-16 code units required for the given code unit sequence when transcoded to UTF-16, and a Boolean value indicating whether the sequence was found to contain only ASCII characters.

iOS 8.0+iPadOS 8.0+Mac Catalyst 13.0+macOS 10.10+tvOS 9.0+visionOS 1.0+watchOS 2.0+

``` source
static func transcodedLength(
    of input: Input,
    decodedAs sourceEncoding: Encoding.Type,
    repairingIllFormedSequences: Bool
) -> (count: Int, isASCII: Bool)? where Input : IteratorProtocol, Encoding : _UnicodeEncoding, Input.Element == Encoding.CodeUnit
```

## Parameters 

`input`  

An iterator of code units to be translated, encoded as `sourceEncoding`. If `repairingIllFormedSequences` is `true`, the entire iterator will be exhausted. Otherwise, iteration will stop if an ill-formed sequence is detected.

`sourceEncoding`  

The Unicode encoding of `input`.

`repairingIllFormedSequences`  

Pass `true` to measure the length of `input` even when `input` contains ill-formed sequences. Each ill-formed sequence is replaced with a Unicode replacement character (`"\u{FFFD}"`) and is measured as such. Pass `false` to immediately stop measuring `input` when an ill-formed sequence is encountered.

## Return Value

A tuple containing the number of UTF-16 code units required to encode `input` and a Boolean value that indicates whether the `input` contained only ASCII characters. If `repairingIllFormedSequences` is `false` and an ill-formed sequence is detected, this method returns `nil`.

## Discussion

The following example finds the length of the UTF-16 encoding of the string `"Fermata 𝄐"`, starting with its UTF-8 representation.

```
let fermata = "Fermata 𝄐"
let bytes = fermata.utf8
print(Array(bytes))
// Prints "[70, 101, 114, 109, 97, 116, 97, 32, 240, 157, 132, 144]"

let result = UTF16.transcodedLength(of: bytes.makeIterator(),
                                    decodedAs: UTF8.self,
                                    repairingIllFormedSequences: false)
print(result)
// Prints "Optional((count: 10, isASCII: false))"
```

