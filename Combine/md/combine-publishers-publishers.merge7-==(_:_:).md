

- Combine
- Publishers
- Publishers.Merge7
-  ==(\_:\_:) 

Operator

# ==(\_:\_:)

Returns a Boolean value that indicates whether two publishers are equivalent.

iOS 13.0+iPadOS 13.0+Mac Catalyst 13.0+macOS 10.15+tvOS 13.0+visionOS 1.0+watchOS 6.0+

``` source
static func == (lhs: Publishers.Merge7, rhs: Publishers.Merge7) -> Bool
```

Available when `A` conforms to `Publisher`, `A` conforms to `Equatable`, `B` conforms to `Publisher`, `B` conforms to `Equatable`, `C` conforms to `Publisher`, `C` conforms to `Equatable`, `D` conforms to `Publisher`, `D` conforms to `Equatable`, `E` conforms to `Publisher`, `E` conforms to `Equatable`, `F` conforms to `Publisher`, `F` conforms to `Equatable`, `G` conforms to `Publisher`, `G` conforms to `Equatable`, `A.Failure` is `B.Failure`, `A.Output` is `B.Output`, `B.Failure` is `C.Failure`, `B.Output` is `C.Output`, `C.Failure` is `D.Failure`, `C.Output` is `D.Output`, `D.Failure` is `E.Failure`, `D.Output` is `E.Output`, `E.Failure` is `F.Failure`, `E.Output` is `F.Output`, `F.Failure` is `G.Failure`, and `F.Output` is `G.Output`.

## Parameters 

`lhs`  

A merging publisher to compare for equality.

`rhs`  

Another merging publisher to compare for equality.

## Return Value

`true` if the two merging publishers have equal source publishers; otherwise `false`.

## See Also

### Comparing Publishers

static func != (Self, Self) -> Bool

Returns a Boolean value indicating whether two values are not equal.

