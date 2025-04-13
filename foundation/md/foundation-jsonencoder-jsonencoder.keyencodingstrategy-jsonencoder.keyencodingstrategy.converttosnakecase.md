

- Foundation
- JSONEncoder
- JSONEncoder.KeyEncodingStrategy
-  JSONEncoder.KeyEncodingStrategy.convertToSnakeCase 

Case

# JSONEncoder.KeyEncodingStrategy.convertToSnakeCase

A key encoding strategy that converts camel-case keys to snake-case keys.

iOS 8.0+iPadOS 8.0+Mac Catalyst 8.0+macOS 10.10+tvOS 9.0+visionOS 1.0+watchOS 2.0+

``` source
case convertToSnakeCase
```

## Discussion

Camel-case and snake-case are two common approaches for combining words when naming parts of an API. The Swift API Design Guidelines recommend using camel-case names. Some JSON APIs adopt snake-case; use this strategy when you encounter such an API.

This strategy uses uppercaseLetters and lowercaseLetters to determine the boundaries between words, and the system locale when converting uppercase letters to lowercase letters.

This strategy follows these steps to convert key names to snake-case:

1.  Split the name into words, preserving leading or trailing underscores.

2.  Insert an underscore between each word.

3.  Convert the resulting string to lowercase.

The following examples show the result of applying this strategy:

`feeFiFoFum`  
Converts to: `fee_fi_fo_fum`

`fee_fi_fo_fum`  
Converts to: `fee_fi_fo_fum`

`xmlContents`  
Converts to: `xml_contents`

The example below shows how properties on the `OlympicEventResult` structure convert to snake-case when encoded as keys in a JSON object.

```
struct OlympicEventResult: Codable {
    var goldWinner: String
    var silverWinner: String
    var bronzeWinner: String
}

let marathonResult = OlympicEventResult(goldWinner: "Light", silverWinner: "Sound", bronzeWinner: "Unladen Swallow")

let encoder = JSONEncoder()
encoder.outputFormatting = [.prettyPrinted, .sortedKeys]
let encodeAndPrint = { print(String(data: try! encoder.encode(marathonResult), encoding: .utf8)!) }

encoder.keyEncodingStrategy = .convertToSnakeCase
encodeAndPrint()

/* Prints:
{
  "bronze_winner" : "Unladen Swallow",
  "gold_winner" : "Light",
  "silver_winner" : "Sound"
}
*/
```

## See Also

### Related Documentation

case convertFromSnakeCase

A key decoding strategy that converts snake-case keys to camel-case keys.

### Built-in Encoding

case useDefaultKeys

A key encoding strategy that doesn’t change key names during encoding.

