

- Foundation
- Formatter
-  getObjectValue(\_:for:errorDescription:) 

Instance Method

# getObjectValue(\_:for:errorDescription:)

The default implementation of this method raises an exception.

iOS 2.0+iPadOS 2.0+Mac Catalyst 13.0+macOS 10.0+tvOS 9.0+visionOS 1.0+watchOS 2.0+

``` source
func getObjectValue(
    _ obj: AutoreleasingUnsafeMutablePointer?,
    for string: String,
    errorDescription error: AutoreleasingUnsafeMutablePointer?
) -> Bool
```

## Parameters 

`obj`  

If conversion is successful, upon return contains the object created from `string`.

`string`  

The string to parse.

`error`  

If non-`nil`, if there is a error during the conversion, upon return contains an `NSString` object that describes the problem.

## Return Value

true if the conversion from string to cell content object was successful, otherwise false.

## Discussion

When implementing this method in a subclass, return by reference the object `anObject` created from `string`. If `string` is equal to the value of the converted object, such as for formatters whose converted value type is `NSString`, it can be returned by reference without creating a new object.

Return true if the conversion is successful. If you return false, also return by indirection (in `error`) a localized user-presentable `NSString` object that explains the reason why the conversion failed; the delegate (if any) of the `NSControl` object managing the cell can then respond to the failure in control:didFailToFormatString:errorDescription:. However, if `error` is `nil`, the sender is not interested in the error description, and you should not attempt to assign one.

The following example (which is paired with the example given in string(for:)) converts a string representation of a dollar amount that includes the dollar sign; it uses an `NSScanner` instance to convert this amount to a float after stripping out the initial dollar sign.

```
- (BOOL)getObjectValue:(id *)obj forString:(NSString *)string errorDescription:(NSString  **)error {
    float floatResult;
    NSScanner *scanner;
    BOOL returnValue = NO;

    scanner = [NSScanner scannerWithString: string];
    [scanner scanString: @"$" intoString: NULL]; // ignore  return value
    if ([scanner scanFloat:&floatResult] && ([scanner isAtEnd])) {
        returnValue = YES;
        if (obj) {
            *obj = [NSNumber numberWithFloat:floatResult];
        }
    } else {
        if (error) {
            *error = NSLocalizedString(@"Couldn’t convert  to float", @"Error converting");
        }
    }
    return returnValue;
}
```

### Special Considerations

Prior to OS X v10.6, the implementation of this method in both NumberFormatter and DateFormatter would return true and an object value even if only part of the string could be parsed. This is problematic because you cannot be sure what portion of the string was parsed. For applications linked on or after OS X v10.6, this method instead returns an error if part of the string cannot be parsed. You can use `getObjectValue:forString:range:error:` to get the old behavior—it returns the range of the substring that was successfully parsed.

## See Also

### Related Documentation

func string(for: Any?) -> String?

The default implementation of this method raises an exception.

