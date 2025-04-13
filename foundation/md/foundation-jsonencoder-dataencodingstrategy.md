

- Foundation
- JSONEncoder
-  dataEncodingStrategy 

Instance Property

# dataEncodingStrategy

The strategy that an encoder uses to encode raw data.

iOS 8.0+iPadOS 8.0+Mac Catalyst 8.0+macOS 10.10+tvOS 9.0+visionOS 1.0+watchOS 2.0+

``` source
var dataEncodingStrategy: JSONEncoder.DataEncodingStrategy { get set }
```

## Discussion

The default strategy is the JSONEncoder.DataEncodingStrategy.base64 strategy.

## See Also

### Encoding Raw Data

enum DataEncodingStrategy

The strategies for encoding raw data.

