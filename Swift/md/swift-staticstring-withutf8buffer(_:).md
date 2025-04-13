

- Swift
- StaticString
-  withUTF8Buffer(\_:) 

Instance Method

# withUTF8Buffer(\_:)

Invokes the given closure with a buffer containing the static string’s UTF-8 code unit sequence (excluding the null terminator).

iOS 8.0+iPadOS 8.0+Mac Catalyst 13.0+macOS 10.10+tvOS 9.0+visionOS 1.0+watchOS 2.0+

``` source
func withUTF8Buffer(_ body: (UnsafeBufferPointer) -> R) -> R
```

## Parameters 

`body`  

A closure that takes a buffer pointer to the static string’s UTF-8 code unit sequence as its sole argument. If the closure has a return value, that value is also used as the return value of the `withUTF8Buffer(_:)` method. The pointer argument is valid only for the duration of the method’s execution.

## Return Value

The return value, if any, of the `body` closure.

## Discussion

This method works regardless of whether the static string stores a pointer or a single Unicode scalar value.

The pointer argument to `body` is valid only during the execution of `withUTF8Buffer(_:)`. Do not store or return the pointer for later use.

