

- Foundation
- HTTPURLResponse
-  value(forHTTPHeaderField:) 

Instance Method

# value(forHTTPHeaderField:)

Returns the value that corresponds to the given header field.

iOS 13.0+iPadOS 13.0+Mac Catalyst 13.1+macOS 10.15+tvOS 13.0+visionOS 1.0+watchOS 6.0+

``` source
func value(forHTTPHeaderField field: String) -> String?
```

## Parameters 

`field`  

The name of the header field you want to retrieve. The name is case-insensitive.

## Return Value

The value associated with the given header field, or `nil` if no value is associated with the field.

## Discussion

In keeping with the HTTP RFC, HTTP header field names are case-insensitive.

## See Also

### Getting HTTP response headers

var allHeaderFields: [AnyHashable : Any]

All HTTP header fields of the response.

