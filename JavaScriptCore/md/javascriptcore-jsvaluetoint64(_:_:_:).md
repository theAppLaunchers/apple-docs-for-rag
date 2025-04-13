

- JavaScriptCore
-  JSValueToInt64(\_:\_:\_:) 

Function

# JSValueToInt64(\_:\_:\_:)

iOS 18.0+iPadOS 18.0+Mac Catalyst 18.0+macOS 15.0+tvOS 9.0+visionOS 2.0+

``` source
func JSValueToInt64(
    _ ctx: JSContextRef,
    _ value: JSValueRef,
    _ exception: UnsafeMutablePointer?
) -> Int64
```

## Discussion

```
@function
@abstract         Converts a JSValue to a singed 64-bit integer and returns the resulting integer.
@param ctx        The execution context to use.
@param value      The JSValue to convert.
@param exception  A pointer to a JSValueRef in which to store an exception, if any. To reliable detect exception, initialize this to null before the call. Pass NULL if you do not care to store an exception.
@result           An int64_t with the result of conversion, or 0 if an exception is thrown. Since 0 is valid value, `exception` must be checked after the call.
@discussion       The JSValue is converted to an integer according to the rules specified by the JavaScript language. If the value is a BigInt, then the JSValue is truncated to an int64_t.
```

