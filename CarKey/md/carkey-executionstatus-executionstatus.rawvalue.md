

- CarKey
- ExecutionStatus
-  ExecutionStatus.RawValue 

Type Alias

# ExecutionStatus.RawValue

The raw type that can be used to represent all values of the conforming type.

iOS 16.0+iPadOS 16.0+Mac Catalyst 16.0+macOS 13.3+watchOS 9.0+

``` source
typealias RawValue = Int
```

## Discussion

Every distinct value of the conforming type has a corresponding unique value of the `RawValue` type, but there may be values of the `RawValue` type that don’t have a corresponding value of the conforming type.

