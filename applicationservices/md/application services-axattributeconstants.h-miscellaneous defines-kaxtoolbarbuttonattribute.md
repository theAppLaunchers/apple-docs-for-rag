

- Application Services
- AXAttributeConstants.h
- Miscellaneous Defines
-  kAXToolbarButtonAttribute 

Global Variable

# kAXToolbarButtonAttribute

macOS 10.2+

``` source
var kAXToolbarButtonAttribute: String { get }
```

## Discussion

The toolbar button of the window represented by this accessibility object. An accessibility object includes this attribute to help an assistive application easily find a window’s toolbar button, without having to traverse the accessibility hierarchy. This attribute is recommended for all accessibility objects that represent windows that contain a toolbar button.

