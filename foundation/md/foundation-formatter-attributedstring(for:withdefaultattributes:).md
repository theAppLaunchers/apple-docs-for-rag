

- Foundation
- Formatter
-  attributedString(for:withDefaultAttributes:) 

Instance Method

# attributedString(for:withDefaultAttributes:)

The default implementation returns `nil` to indicate that the formatter object does not provide an attributed string.

iOS 2.0+iPadOS 2.0+Mac Catalyst 13.0+macOS 10.0+tvOS 9.0+visionOS 1.0+watchOS 2.0+

``` source
func attributedString(
    for obj: Any,
    withDefaultAttributes attrs: [NSAttributedString.Key : Any]? = nil
) -> NSAttributedString?
```

## Parameters 

`obj`  

The object for which a textual representation is returned.

`attrs`  

The default attributes to use for the returned attributed string.

## Return Value

An attributed string that represents `anObject`.

## Discussion

When implementing a subclass, return an `NSAttributedString` object if the string for display should have some attributes. For instance, you might want negative values in a financial application to appear in red text. Invoke your implementation of string(for:) to get the non-attributed string, then create an `NSAttributedString` object with it (see init(string:)). Use the `attributes` default dictionary to reset the attributes of the string when a change in value warrants it (for example, a negative value becomes positive) For information on creating attributed strings, see Attributed String Programming Guide.

## See Also

### Getting Textual Representations of Object Values

func string(for: Any?) -> String?

The default implementation of this method raises an exception.

func editingString(for: Any) -> String?

The default implementation of this method invokes string(for:).

