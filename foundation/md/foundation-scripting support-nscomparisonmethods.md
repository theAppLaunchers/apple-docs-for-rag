

- Foundation
- Scripting Support
-  NSComparisonMethods 

# NSComparisonMethods

A collection of default comparison methods useful for performing specifier tests.

## Overview

If you have scriptable objects that need to perform comparisons for scripting purposes, you may need to implement some of the methods declared in NSScriptingComparisonMethods. The default implementation provided for many of these methods by `NSObject` is appropriate for objects that implement a single comparison method whose selector, signature, and description match the following:

```
- (NSComparisonResult)compare:(id)object;
```

This method should return `NSOrderedAscending` if the receiver is less than `object`, `NSOrderedDescending` if the receiver is greater than `object`, and `NSOrderedSame` if the receiver and `object` are equal. For example, `NSString` does not implement most of the methods declared in this informal protocol, but `NSString` objects still handle messages conforming to this protocol properly because `NSString` implements a `compare:` method that meets the necessary requirements. Cocoa also includes appropriate `compare:` method implementations for the `NSDate`, `NSDecimalNumber`, and `NSValue` classes.

## Topics

### Performing comparisons

func doesContain(_ object: Any) -> Bool

Returns a Boolean value that indicates whether the receiver contains a given object.

func isCaseInsensitiveLike(_ object: String) -> Bool

Returns a Boolean value that indicates whether receiver is considered to be “like” a given string when the case of characters in the receiver is ignored.

func isEqual(to object: Any?) -> Bool

Returns a Boolean value that indicates whether the receiver is equal to another given object.

func isGreaterThan(_ object: Any?) -> Bool

Returns a Boolean value that indicates whether the receiver is greater than another given object.

func isGreaterThanOrEqual(to object: Any?) -> Bool

Returns a Boolean value that indicates whether the receiver is greater than or equal to another given object.

func isLessThan(_ object: Any?) -> Bool

Returns a Boolean value that indicates whether the receiver is less than another given object.

func isLessThanOrEqual(to object: Any?) -> Bool

Returns a Boolean value that indicates whether the receiver is less than or equal to another given object.

func isLike(_ object: String) -> Bool

Returns a Boolean value that indicates whether the receiver is “like” another given object.

func isNotEqual(to object: Any?) -> Bool

Returns a Boolean value that indicates whether the receiver is not equal to another given object.

## See Also

### Related Documentation

Cocoa Scripting Guide

### NSObject Script Support

NSScriptingComparisonMethods

A collection of methods useful for comparing script objects.

NSScriptKeyValueCoding

A collection of methods that provide additional capabilities for working with key-value coding.

NSScriptObjectSpecifiers

A collection of methods providing additional object specifier functionality.

class NSScriptCoercionHandler

A mechanism for converting one kind of scripting data to another.

class NSScriptExecutionContext

The context in which the current script command is executed.

