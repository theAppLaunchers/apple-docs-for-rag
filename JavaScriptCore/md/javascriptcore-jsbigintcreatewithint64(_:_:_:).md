

- JavaScriptCore
-  JSBigIntCreateWithInt64(\_:\_:\_:) 

Function

# JSBigIntCreateWithInt64(\_:\_:\_:)

iOS 18.0+iPadOS 18.0+Mac Catalyst 18.0+macOS 15.0+tvOS 9.0+visionOS 2.0+

``` source
func JSBigIntCreateWithInt64(
    _ ctx: JSContextRef,
    _ integer: Int64,
    _ exception: UnsafeMutablePointer?
) -> JSValueRef
```

## Discussion

```
@function
@abstract         Creates a JavaScript BigInt with a 64-bit signed integer.
@param ctx        The execution context to use.
@param integer    The 64-bit signed integer to copy into the new BigInt JSValue.
@param exception  A pointer to a JSValueRef in which to store an exception, if any. To reliable detect exception, initialize this to null before the call. Pass NULL if you do not care to store an exception.
@result           A BigInt JSValue of the integer, or NULL if an exception is thrown.
```

