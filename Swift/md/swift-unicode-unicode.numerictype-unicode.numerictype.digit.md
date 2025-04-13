

- Swift
- Unicode
- Unicode.NumericType
-  Unicode.NumericType.digit 

Case

# Unicode.NumericType.digit

A digit that does not meet the requirements of the `decimal` numeric type.

iOS 8.0+iPadOS 8.0+Mac Catalyst 13.0+macOS 10.10+tvOS 9.0+visionOS 1.0+watchOS 2.0+

``` source
case digit
```

## Discussion

Scalars with this numeric type are often those that represent a decimal digit but would not typically be used to write a base-10 number, such as “④” (U+2463 CIRCLED DIGIT FOUR).

As of Unicode 6.3, any new scalars that represent numbers but do not meet the requirements of `decimal` will have numeric type `numeric`, and programs can treat `digit` and `numeric` equivalently.

