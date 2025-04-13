

- Swift
- Unmanaged
-  takeUnretainedValue() 

Instance Method

# takeUnretainedValue()

Gets the value of this unmanaged reference as a managed reference without consuming an unbalanced retain of it.

iOS 8.0+iPadOS 8.0+Mac Catalyst 13.0+macOS 10.10+tvOS 9.0+visionOS 1.0+watchOS 2.0+

``` source
func takeUnretainedValue() -> Instance
```

## Return Value

The object referenced by this `Unmanaged` instance.

## Discussion

This is useful when a function returns an unmanaged reference and you know that you’re not responsible for releasing the result.

