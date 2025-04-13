

- Core Transferable
- TransferRepresentationBuilder
-  buildBlock(\_:\_:\_:\_:\_:\_:\_:\_:\_:\_:) 

Type Method

# buildBlock(\_:\_:\_:\_:\_:\_:\_:\_:\_:\_:)

Combines multiple transfer representations into a single transfer representation.

iOS 16.0+iPadOS 16.0+Mac Catalyst 16.0+macOS 13.0+tvOS 16.0+visionOS 1.0+watchOS 9.0+

``` source
static func buildBlock(
    _ content1: C1,
    _ content2: C2,
    _ content3: C3,
    _ content4: C4,
    _ content5: C5,
    _ content6: C6,
    _ content7: C7,
    _ content8: C8,
    _ content9: C9,
    _ content10: C10
) -> TupleTransferRepresentation where Item == C1.Item, C1 : TransferRepresentation, C2 : TransferRepresentation, C3 : TransferRepresentation, C4 : TransferRepresentation, C5 : TransferRepresentation, C6 : TransferRepresentation, C7 : TransferRepresentation, C8 : TransferRepresentation, C9 : TransferRepresentation, C10 : TransferRepresentation, C1.Item == C2.Item, C2.Item == C3.Item, C3.Item == C4.Item, C4.Item == C5.Item, C5.Item == C6.Item, C6.Item == C7.Item, C7.Item == C8.Item, C8.Item == C9.Item, C9.Item == C10.Item
```

## See Also

### Combining transfer representations

static func buildBlock&lt;C1, C2>(C1, C2) -> TupleTransferRepresentation&lt;Item, (C1, C2)>

Combines multiple transfer representations into a single transfer representation.

static func buildBlock&lt;C1, C2, C3>(C1, C2, C3) -> TupleTransferRepresentation&lt;Item, (C1, C2, C3)>

Combines multiple transfer representations into a single transfer representation.

static func buildBlock&lt;C1, C2, C3, C4>(C1, C2, C3, C4) -> TupleTransferRepresentation&lt;Item, (C1, C2, C3, C4)>

Combines multiple transfer representations into a single transfer representation.

static func buildBlock&lt;C1, C2, C3, C4, C5>(C1, C2, C3, C4, C5) -> TupleTransferRepresentation&lt;Item, (C1, C2, C3, C4, C5)>

Combines multiple transfer representations into a single transfer representation.

static func buildBlock&lt;C1, C2, C3, C4, C5, C6>(C1, C2, C3, C4, C5, C6) -> TupleTransferRepresentation&lt;Item, (C1, C2, C3, C4, C5, C6)>

Combines multiple transfer representations into a single transfer representation.

static func buildBlock&lt;C1, C2, C3, C4, C5, C6, C7>(C1, C2, C3, C4, C5, C6, C7) -> TupleTransferRepresentation&lt;Item, (C1, C2, C3, C4, C5, C6, C7)>

Combines multiple transfer representations into a single transfer representation.

static func buildBlock&lt;C1, C2, C3, C4, C5, C6, C7, C8>(C1, C2, C3, C4, C5, C6, C7, C8) -> TupleTransferRepresentation&lt;Item, (C1, C2, C3, C4, C5, C6, C7, C8)>

Combines multiple transfer representations into a single transfer representation.

static func buildBlock&lt;C1, C2, C3, C4, C5, C6, C7, C8, C9>(C1, C2, C3, C4, C5, C6, C7, C8, C9) -> TupleTransferRepresentation&lt;Item, (C1, C2, C3, C4, C5, C6, C7, C8, C9)>

Combines multiple transfer representations into a single transfer representation.

