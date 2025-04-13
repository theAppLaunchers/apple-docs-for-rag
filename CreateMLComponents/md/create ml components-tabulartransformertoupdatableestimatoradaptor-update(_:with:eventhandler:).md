

- Create ML Components
- TabularTransformerToUpdatableEstimatorAdaptor
-  update(\_:with:eventHandler:) 

Instance Method

# update(\_:with:eventHandler:)

Does nothing since this estimator uses a pre-defined transformer.

iOS 16.0+iPadOS 16.0+Mac Catalyst 16.0+macOS 13.0+tvOS 16.0+visionOS 1.0+watchOS 11.0+

``` source
func update(
    _ transformer: inout Transformer,
    with input: DataFrame,
    eventHandler: EventHandler? = nil
) async throws
```

## See Also

### Fitting

func fitted(to: DataFrame, eventHandler: EventHandler?) async throws -> Transformer

Returns the pre-defined transformer.

