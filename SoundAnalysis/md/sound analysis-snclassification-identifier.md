

- Sound Analysis
- SNClassification
-  identifier 

Instance Property

# identifier

A prediction label that’s one of the classifications a sound classifier’s underlying model defines.

iOS 13.0+iPadOS 13.0+Mac Catalyst 13.1+macOS 10.15+tvOS 13.0+visionOS 1.0+watchOS 6.0+

``` source
var identifier: String { get }
```

## Discussion

An example `identifier` might be a string like `laughter` or `applause`*.* The sound classifier’s underlying model defines the possible string values, which are typically technical names that you don’t directly present in your app’s user interface.

## See Also

### Inspecting a Classification

var confidence: Double

The confidence value the model has in its prediction.

