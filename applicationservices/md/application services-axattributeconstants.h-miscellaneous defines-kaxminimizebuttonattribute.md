

- Application Services
- AXAttributeConstants.h
- Miscellaneous Defines
-  kAXMinimizeButtonAttribute 

Global Variable

# kAXMinimizeButtonAttribute

macOS 10.2+

``` source
var kAXMinimizeButtonAttribute: String { get }
```

## Discussion

The minimize button of the window represented by this accessibility object. An accessibility object includes this attribute to help an assistive application easily find a window’s minimize button, without having to traverse the accessibility hierarchy. This attribute is recommended for all accessibility objects that represent windows that contain a minimize button.

