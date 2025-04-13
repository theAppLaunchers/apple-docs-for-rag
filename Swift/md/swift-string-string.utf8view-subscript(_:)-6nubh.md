

- Swift
- String
- String.UTF8View
-  subscript(\_:) 

Instance Subscript

# subscript(\_:)

Accesses the code unit at the given position.

iOS 8.0+iPadOS 8.0+Mac Catalyst 13.0+macOS 10.10+tvOS 9.0+visionOS 1.0+watchOS 2.0+

``` source
subscript(i: String.UTF8View.Index) -> UTF8.CodeUnit { get }
```

## Overview

The following example uses the subscript to print the value of a string’s first UTF-8 code unit.

```
let greeting = "Hello, friend!"
let i = greeting.utf8.startIndex
print("First character's UTF-8 code unit: \(greeting.utf8[i])")
// Prints "First character's UTF-8 code unit: 72"
```

