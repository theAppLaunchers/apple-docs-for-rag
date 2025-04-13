

- AppKit
-  NSAccessibilityImage 

Protocol

# NSAccessibilityImage

A role-based protocol that declares the minimum interface necessary for an accessibility element to act as an image.

macOS

``` source
protocol NSAccessibilityImage : NSAccessibilityElementProtocol
```

## Overview

Use this protocol when you want a user interface element to behave like an image\_ \_in the accessibility hierarchy.

You can further enhance the adopting element by implementing any of the information properties or action methods that the NSAccessibilityProtocol protocol declares.

Explicit Implementation Required

Any class that adopts this protocol must implement all of its methods, and the required methods of any protocol it inherits from. The compiler may require you to override some methods that your ancestors have already implemented. Simply follow the compiler’s warnings, and reimplement these methods as necessary.

## Topics

### Supporting Accessibility

func accessibilityLabel() -> String?

Returns a short description of the image’s label.

**Required**

## Relationships

### Inherits From

- NSAccessibilityElementProtocol
- NSObjectProtocol

### Conforming Types

- NSImageView

## See Also

### Images and Color

protocol NSAccessibilityColor

A role-based protocol that declares the minimum interface necessary for an accessibility element to act as a color.

