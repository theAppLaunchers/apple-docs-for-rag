

- Swift
- ArraySlice
-  subscript(\_:) 

Instance Subscript

# subscript(\_:)

Accesses the element at the specified position.

iOS 8.0+iPadOS 8.0+Mac Catalyst 13.0+macOS 10.10+tvOS 9.0+visionOS 1.0+watchOS 2.0+

``` source
subscript(index: Int) -> Element { get set }
```

## Parameters 

`index`  

The position of the element to access. `index` must be greater than or equal to `startIndex` and less than `endIndex`.

## Overview

The following example uses indexed subscripting to update an array’s second element. After assigning the new value (`"Butler"`) at a specific position, that value is immediately available at that same position.

```
var streets = ["Adams", "Bryant", "Channing", "Douglas", "Evarts"]
streets[1] = "Butler"
print(streets[1])
// Prints "Butler"
```

Complexity

Reading an element from an array is O(1). Writing is O(1) unless the array’s storage is shared with another array or uses a bridged `NSArray` instance as its storage, in which case writing is O(*n*), where *n* is the length of the array.

