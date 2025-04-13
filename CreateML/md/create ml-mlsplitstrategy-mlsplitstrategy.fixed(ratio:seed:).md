

- Create ML
- MLSplitStrategy
-  MLSplitStrategy.fixed(ratio:seed:) 

Case

# MLSplitStrategy.fixed(ratio:seed:)

Create ML uses a portion of your training dataset to create a validation dataset based on the ratio.

iOS 15.0+iPadOS 15.0+Mac Catalyst 15.0+macOS 10.15+tvOS 16.0+visionOS 1.0+

``` source
case fixed(
    ratio: Double,
    seed: Int?
)
```

## Discussion

Use a value in the range `[0.0, 1.0]` for `ratio`. Use any value for `seed`, including the return value from timestampSeed(), to tell Create ML how to pseudorandomly select data from your training dataset. Otherwise, set `seed` to `nil` to tell Create ML to choose a number for you.

## See Also

### Partitioning data

case automatic

Create ML automatically decides how much of your training dataset it uses for a validation dataset.

func resolve(count: Int) -> (ratio: Double, seed: Int)

Resolves this split strategy for a specific element count.

