

- Create ML
- MLSplitStrategy
-  resolve(count:) 

Instance Method

# resolve(count:)

Resolves this split strategy for a specific element count.

iOS 15.0+iPadOS 15.0+Mac Catalyst 15.0+macOS 11.0+tvOS 16.0+visionOS 1.0+

``` source
func resolve(count: Int) -> (ratio: Double, seed: Int)
```

## Parameters 

`count`  

The number of elements in the collection being split.

## Return Value

The split fraction and the random seed to use.

## See Also

### Partitioning data

case automatic

Create ML automatically decides how much of your training dataset it uses for a validation dataset.

case fixed(ratio: Double, seed: Int?)

Create ML uses a portion of your training dataset to create a validation dataset based on the ratio.

