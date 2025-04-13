

- Application Services
- AXAttributeConstants.h
- Miscellaneous Defines
-  kAXAllowedValuesAttribute 

Global Variable

# kAXAllowedValuesAttribute

macOS 10.4+

``` source
var kAXAllowedValuesAttribute: String { get }
```

## Discussion

An array of the allowed values for an accessibility object. This attribute indicates the subset of values to which an accessibility object can be set. For example, a slider control displays a large range of values, but the accessibility object representing the slider can be set to only a few specific values within that range. This attribute is used only in conjunction with the `AXValue` attribute.

