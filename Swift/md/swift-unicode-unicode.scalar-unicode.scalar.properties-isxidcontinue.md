

- Swift
- Unicode
- Unicode.Scalar
- Unicode.Scalar.Properties
-  isXIDContinue 

Instance Property

# isXIDContinue

A Boolean value indicating whether the scalar is one which is recommended to be allowed to appear in a non-starting position in a programming language identifier, with adjustments made for NFKC normalized form.

iOS 8.0+iPadOS 8.0+Mac Catalyst 13.0+macOS 10.10+tvOS 9.0+visionOS 1.0+watchOS 2.0+

``` source
var isXIDContinue: Bool { get }
```

## Discussion

The set of scalars `[:XID_Continue:]` closes the set `[:ID_Continue:]` under NFKC normalization by removing any scalars whose normalized form is not of the form `[:ID_Continue:]*`.

This property corresponds to the “XID_Continue” property in the Unicode Standard.

