

- Swift
- Encoder
-  singleValueContainer() 

Instance Method

# singleValueContainer()

Returns an encoding container appropriate for holding a single primitive value.

iOS 8.0+iPadOS 8.0+Mac Catalyst 13.0+macOS 10.10+tvOS 9.0+visionOS 1.0+watchOS 2.0+

``` source
func singleValueContainer() -> any SingleValueEncodingContainer
```

**Required**

## Return Value

A new empty single value container.

## Discussion

You must use only one kind of top-level encoding container. This method must not be called after a call to `unkeyedContainer()` or `container(keyedBy:)`, or after encoding a value through a call to `singleValueContainer()`

