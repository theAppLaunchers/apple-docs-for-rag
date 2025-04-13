

- PHASE
- PHASEBlendNodeDefinition
-  addRangeForInputValuesBetween(lowValue:highValue:fullGainAtLowValue:fullGainAtHighValue:lowFadeCurveType:highFadeCurveType:subtree:) 

Instance Method

# addRangeForInputValuesBetween(lowValue:highValue:fullGainAtLowValue:fullGainAtHighValue:lowFadeCurveType:highFadeCurveType:subtree:)

Adds a child node that blends between a given high and low value.

iOS 15.0+iPadOS 15.0+Mac Catalyst 15.0+macOS 12.0+tvOS 17.0+visionOS 1.0+

``` source
func addRangeForInputValuesBetween(
    lowValue: Double,
    highValue: Double,
    fullGainAtLowValue: Double,
    fullGainAtHighValue: Double,
    lowFadeCurveType: PHASECurveType,
    highFadeCurveType: PHASECurveType,
    subtree: PHASESoundEventNodeDefinition
)
```

## Parameters 

`lowValue`  

A value above which the child node blends.

`highValue`  

A value below which the child node blends.

`fullGainAtLowValue`  

The threshold for which a fade curve that `lowFadeCurveType` defines applies to the gain when the blend parameter value is between `lowValue` and `fullGainAtLowValue`.

`fullGainAtHighValue`  

The threshold for which a fade curve that `highFadeCurveType` defines applies to the gain when the blend parameter value is between `highValue` and `fullGainAtHighValue`.

`lowFadeCurveType`  

An option that determines a rate of change for the child node’s gain over the low fade range.

`highFadeCurveType`  

An option that determines a rate of change for the child node’s gain over the high fade range.

`subtree`  

A child node to blend.

## See Also

### Adding Child Nodes

func addRange(envelope: PHASEEnvelope, subtree: PHASESoundEventNodeDefinition)

Adds a child node with an envelope.

func addRangeForInputValuesAbove(value: Double, fullGainAtValue: Double, fadeCurveType: PHASECurveType, subtree: PHASESoundEventNodeDefinition)

Adds a child node that blends above a given value.

func addRangeForInputValuesBelow(value: Double, fullGainAtValue: Double, fadeCurveType: PHASECurveType, subtree: PHASESoundEventNodeDefinition)

Adds a child node that blends below a given value.

