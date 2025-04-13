

- Foundation
- ValueTransformer
-  transformedValue(\_:) 

Instance Method

# transformedValue(\_:)

Returns the result of transforming a given value.

iOS 3.0+iPadOS 3.0+Mac Catalyst 13.1+macOS 10.3+tvOS 9.0+visionOS 1.0+watchOS 2.0+

``` source
func transformedValue(_ value: Any?) -> Any?
```

## Parameters 

`value`  

The value to transform.

## Return Value

The result of transforming `value`.

The default implementation simply returns `value`.

## Discussion

A subclass should override this method to transform and return an object based on `value`.

## See Also

### Transforming Values

func reverseTransformedValue(Any?) -> Any?

Returns the result of the reverse transformation of a given value.

