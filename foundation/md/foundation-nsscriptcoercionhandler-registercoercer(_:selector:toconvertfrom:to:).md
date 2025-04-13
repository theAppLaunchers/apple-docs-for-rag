

- Foundation
- NSScriptCoercionHandler
-  registerCoercer(\_:selector:toConvertFrom:to:) 

Instance Method

# registerCoercer(\_:selector:toConvertFrom:to:)

Registers a given object (typically a class) to handle coercions (conversions) from one given class to another.

Mac Catalyst 13.0+macOS 10.0+

``` source
func registerCoercer(
    _ coercer: Any,
    selector: Selector,
    toConvertFrom fromClass: AnyClass,
    to toClass: AnyClass
)
```

## Parameters 

`coercer`  

The object that performs the coercion. `coercer` should typically be a class object.

`selector`  

A selector that specifies the method to perform the coercion. `selector` should typically be a factory method, and must take two arguments. The first is the value to be converted. The second is the class to convert it to.

`fromClass`  

The class for which instances are coerced.

`toClass`  

The class to which instances of `fromClass` are coerced.

## See Also

### Working with handlers

func coerceValue(Any, to: AnyClass) -> Any?

Returns an object of a given class representing a given value.

