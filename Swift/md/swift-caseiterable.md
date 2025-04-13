

- Swift
-  CaseIterable 

Protocol

# CaseIterable

A type that provides a collection of all of its values.

iOS 8.0+iPadOS 8.0+Mac Catalyst 13.0+macOS 10.10+tvOS 9.0+visionOS 1.0+watchOS 2.0+

``` source
protocol CaseIterable
```

## Overview

Types that conform to the `CaseIterable` protocol are typically enumerations without associated values. When using a `CaseIterable` type, you can access a collection of all of the type’s cases by using the type’s `allCases` property.

For example, the `CompassDirection` enumeration declared in this example conforms to `CaseIterable`. You access the number of cases and the cases themselves through `CompassDirection.allCases`.

```
enum CompassDirection: CaseIterable {
    case north, south, east, west
}

print("There are \(CompassDirection.allCases.count) directions.")
// Prints "There are 4 directions."
let caseList = CompassDirection.allCases
                               .map({ "\($0)" })
                               .joined(separator: ", ")
// caseList == "north, south, east, west"
```

# Conforming to the CaseIterable Protocol

The compiler can automatically provide an implementation of the `CaseIterable` requirements for any enumeration without associated values or `@available` attributes on its cases. The synthesized `allCases` collection provides the cases in order of their declaration.

You can take advantage of this compiler support when defining your own custom enumeration by declaring conformance to `CaseIterable` in the enumeration’s original declaration. The `CompassDirection` example above demonstrates this automatic implementation.

## Topics

### Accessing Cases

static var allCases: Self.AllCases

A collection of all values of this type.

**Required**

associatedtype AllCases : Collection = [Self]

A type that can represent a collection of all values of this type.

**Required**

## See Also

### Raw Representation

protocol RawRepresentable

A type that can be converted to and from an associated raw value.

