

- Foundation
- JSONDecoder
-  decode(\_:from:) 

Instance Method

# decode(\_:from:)

Returns a value of the type you specify, decoded from a JSON object.

iOS 8.0+iPadOS 8.0+Mac Catalyst 8.0+macOS 10.10+tvOS 9.0+visionOS 1.0+watchOS 2.0+

``` source
func decode(
    _ type: T.Type,
    from data: Data
) throws -> T where T : Decodable
```

## Parameters 

`type`  

The type of the value to decode from the supplied JSON object.

`data`  

The JSON object to decode.

## Return Value

A value of the specified type, if the decoder can parse the data.

## Discussion

If the data isn’t valid JSON, this method throws the DecodingError.dataCorrupted(_:) error. If a value within the JSON fails to decode, this method throws the corresponding error.

