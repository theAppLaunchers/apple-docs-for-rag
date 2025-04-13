

- Swift
- DecodingError
-  DecodingError.Context 

Structure

# DecodingError.Context

The context in which the error occurred.

iOS 8.0+iPadOS 8.0+Mac Catalyst 13.0+macOS 10.10+tvOS 9.0+visionOS 1.0+watchOS 2.0+

``` source
struct Context
```

## Topics

### Initializers

init(codingPath: [any CodingKey], debugDescription: String, underlyingError: (any Error)?)

Creates a new context with the given path of coding keys and a description of what went wrong.

### Instance Properties

let codingPath: [any CodingKey]

The path of coding keys taken to get to the point of the failing decode call.

let debugDescription: String

A description of what went wrong, for debugging purposes.

let underlyingError: (any Error)?

The underlying error which caused this error, if any.

## Relationships

### Conforms To

- Sendable

