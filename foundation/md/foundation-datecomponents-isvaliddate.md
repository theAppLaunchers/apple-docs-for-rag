

- Foundation
- DateComponents
-  isValidDate 

Instance Property

# isValidDate

Indicates whether the current combination of properties represents a date which exists in the current calendar.

iOS 8.0+iPadOS 8.0+Mac Catalyst 8.0+macOS 10.9+tvOS 9.0+visionOS 1.0+watchOS 2.0+

``` source
var isValidDate: Bool { get }
```

## Discussion

This method is not appropriate for use on `DateComponents` values which are specifying relative quantities of calendar components.

Except for some trivial cases (e.g., ‘seconds’ should be 0 - 59 in any calendar), this method is not necessarily cheap.

If the time zone property is set in the `DateComponents`, it is used.

The calendar property must be set, or the result is always `false`.

## See Also

### Validating a Date

func isValidDate(in: Calendar) -> Bool

Indicates whether the current combination of properties represents a date which exists in the specified calendar.

var date: Date?

The date calculated from the current components using the stored calendar.

