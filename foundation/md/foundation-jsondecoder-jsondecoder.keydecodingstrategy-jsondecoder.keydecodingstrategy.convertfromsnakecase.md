

- Foundation
- JSONDecoder
- JSONDecoder.KeyDecodingStrategy
-  JSONDecoder.KeyDecodingStrategy.convertFromSnakeCase 

Case

# JSONDecoder.KeyDecodingStrategy.convertFromSnakeCase

A key decoding strategy that converts snake-case keys to camel-case keys.

iOS 8.0+iPadOS 8.0+Mac Catalyst 8.0+macOS 10.10+tvOS 9.0+visionOS 1.0+watchOS 2.0+

``` source
case convertFromSnakeCase
```

## Discussion

Snake-case and camel-case are two common approaches for combining words when naming parts of an API. The Swift API Design Guidelines recommend using camel-case names. Some JSON APIs adopt snake-case; use this strategy when you encounter such an API.

This strategy uses uppercaseLetters and lowercaseLetters to determine the boundaries between words, and the system locale when capitalizing letters.

This strategy follows these steps to convert JSON keys to camel-case:

1.  Capitalize each word that follows an underscore.

2.  Remove all underscores that aren’t at the very start or end of the string.

3.  Combine the words into a single string.

The following examples show the result of applying this strategy:

`fee_fi_fo_fum`  
Converts to: `feeFiFoFum`

`feeFiFoFum`  
Converts to: `feeFiFoFum`

`base_uri`  
Converts to: `baseUri`

Note

The JSONDecoder.KeyDecodingStrategy.convertFromSnakeCase strategy can’t infer capitalization for acronyms or initialisms such as WYSIWYG or URI. The example above shows how the automatic conversion differs from the conversion you might expect: `baseURI`. To decode such a key with the correct capitalization, define a custom `CodingKeys` enumeration, as described in Encoding and Decoding Custom Types.

The example below shows how properties on the `OlympicEventResult` structure convert from snake-case when decoded as keys in a JSON object.

```
struct OlympicEventResult: Codable {
    var goldWinner: String
    var silverWinner: String
    var bronzeWinner: String
}

let json = """
{
    "silver_winner": "Sound",
    "gold_winner": "Light",
    "bronze_winner": "Unladen Swallow"
}
""".data(using: .utf8)!

let decoder = JSONDecoder()
let decodeAndPrint = { print(try! decoder.decode(OlympicEventResult.self, from: json)) }

decoder.keyDecodingStrategy = .convertFromSnakeCase
decodeAndPrint()

// Prints: "OlympicEventResult(goldWinner: "Light", silverWinner: "Sound", bronzeWinner: "Unladen Swallow")"
```

## See Also

### Related Documentation

case convertToSnakeCase

A key encoding strategy that converts camel-case keys to snake-case keys.

### Built-in Decoding

case useDefaultKeys

A key decoding strategy that doesn’t change key names during decoding.

