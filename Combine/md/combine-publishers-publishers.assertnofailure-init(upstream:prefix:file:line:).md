

- Combine
- Publishers
- Publishers.AssertNoFailure
-  init(upstream:prefix:file:line:) 

Initializer

# init(upstream:prefix:file:line:)

Creates a publisher that raises a fatal error upon receiving any failure, and otherwise republishes all received input.

iOS 13.0+iPadOS 13.0+Mac Catalyst 13.0+macOS 10.15+tvOS 13.0+visionOS 1.0+watchOS 6.0+

``` source
init(
    upstream: Upstream,
    prefix: String,
    file: StaticString,
    line: UInt
)
```

## Parameters 

`upstream`  

The publisher from which this publisher receives elements.

`prefix`  

The string used at the beginning of the fatal error message.

`file`  

The filename used in the error message.

`line`  

The line number used in the error message.

