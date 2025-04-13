

- MusicKit
- MusicLibrary
- MusicLibrary.Error
-  MusicLibrary.Error.RawValue 

Type Alias

# MusicLibrary.Error.RawValue

The raw type that can be used to represent all values of the conforming type.

iOS 16.1+iPadOS 16.1+Mac Catalyst 17.0+macOS 14.0+tvOS 16.1+visionOS 1.0+watchOS 9.1+

``` source
typealias RawValue = String
```

## Discussion

Every distinct value of the conforming type has a corresponding unique value of the `RawValue` type, but there may be values of the `RawValue` type that don’t have a corresponding value of the conforming type.

