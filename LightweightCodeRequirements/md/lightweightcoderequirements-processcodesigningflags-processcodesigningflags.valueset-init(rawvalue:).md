

- LightweightCodeRequirements
- ProcessCodeSigningFlags
- ProcessCodeSigningFlags.ValueSet
-  init(rawValue:) 

Initializer

# init(rawValue:)

Creates a new option set from the given raw value.

iOS 17.4+iPadOS 17.4+Mac Catalyst 17.4+macOS 14.4+tvOS 17.4+visionOS 1.1+watchOS 10.4+

``` source
init(rawValue: Int64)
```

## Parameters 

`rawValue`  

The raw value of the option set to create. Each bit of `rawValue` potentially represents an element of the option set, though raw values may include bits that are not defined as distinct values of the `OptionSet` type.

## Discussion

This initializer always succeeds, even if the value passed as `rawValue` exceeds the static properties declared as part of the option set. This example creates an instance of `ShippingOptions` with a raw value beyond the highest element, with a bit mask that effectively contains all the declared static members.

```
let extraOptions = ShippingOptions(rawValue: 255)
print(extraOptions.isStrictSuperset(of: .all))
// Prints "true"
```

