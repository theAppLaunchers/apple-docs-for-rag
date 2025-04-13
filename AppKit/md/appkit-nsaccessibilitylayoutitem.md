

- AppKit
-  NSAccessibilityLayoutItem 

Protocol

# NSAccessibilityLayoutItem

A role-based protocol that declares the minimum interface necessary for an accessibility element to act as a layout item.

macOS

``` source
protocol NSAccessibilityLayoutItem : NSAccessibilityGroup
```

## Overview

Use this protocol when you want to create a layout item, a repositionable and resizeable item inside a layout area.

You can further enhance the adopting element by implementing any of the information properties or action methods that the NSAccessibilityProtocol protocol declares.

Explicit Implementation Required

Any class that adopts this protocol must implement all of its methods, and the required methods of any protocol it inherits from. The compiler may require you to override some methods that your ancestors have already implemented. Simply follow the compiler’s warnings, and reimplement these methods as necessary.

## Topics

### Supporting Accessibility

func setAccessibilityFrame(NSRect)

Sets the accessibility element’s frame.

## Relationships

### Inherits From

- NSAccessibilityElementProtocol
- NSAccessibilityGroup
- NSObjectProtocol

## See Also

### Layout Elements

protocol NSAccessibilityLayoutArea

A role-based protocol that declares the minimum interface necessary for an accessibility element to act as a layout area.

