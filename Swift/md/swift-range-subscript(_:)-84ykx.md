

- Swift
- Range
-  subscript(\_:) 

Instance Subscript

# subscript(\_:)

Accesses the element at specified position.

iOS 8.0+iPadOS 8.0+Mac Catalyst 13.0+macOS 10.10+tvOS 9.0+visionOS 1.0+watchOS 2.0+

``` source
subscript(position: Range.Index) -> Range.Element { get }
```

Available when `Bound` conforms to `Strideable` and `Bound.Stride` conforms to `SignedInteger`.

## Parameters 

`position`  

The position of the element to access. `position` must be a valid index of the range, and must not equal the range’s end index.

## Overview

You can subscript a collection with any valid index other than the collection’s end index. The end index refers to the position one past the last element of a collection, so it doesn’t correspond with an element.

