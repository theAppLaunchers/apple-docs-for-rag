

- Create ML Components
- UpdatableTabularEstimator
-  update(\_:with:) 

Instance Method

# update(\_:with:)

iOS 16.0+iPadOS 16.0+Mac Catalyst 16.0+macOS 13.0+tvOS 16.0+visionOS 1.0+watchOS 11.0+

``` source
func update(
    _ transformer: inout Self.Transformer,
    with input: DataFrame
) async throws
```

## See Also

### Transforming

func makeTransformer() -> Self.Transformer

Creates a default-initialized transformer suitable for incremental fitting.

**Required**

func update(inout Self.Transformer, with: DataFrame, eventHandler: EventHandler?) async throws

Updates a transformer with a new sequence of examples.

**Required**

