

- JavaScriptCore
-  JSBigIntCreateWithString(\_:\_:\_:) 

Function

# JSBigIntCreateWithString(\_:\_:\_:)

iOS 18.0+iPadOS 18.0+Mac Catalyst 18.0+macOS 15.0+tvOS 9.0+visionOS 2.0+

``` source
func JSBigIntCreateWithString(
    _ ctx: JSContextRef,
    _ string: JSStringRef,
    _ exception: UnsafeMutablePointer?
) -> JSValueRef
```

## Discussion

```
@function
@abstract         Creates a JavaScript BigInt with an integer represented in string.
@param ctx        The execution context to use.
@param string     The JSStringRef representation of an integer.
@param exception  A pointer to a JSValueRef in which to store an exception, if any. To reliable detect exception, initialize this to null before the call. Pass NULL if you do not care to store an exception.
@result           A BigInt JSValue of the string, or NULL if an exception is thrown.
@discussion       This is equivalent to calling the `BigInt` constructor from JavaScript with a string argument.
```

