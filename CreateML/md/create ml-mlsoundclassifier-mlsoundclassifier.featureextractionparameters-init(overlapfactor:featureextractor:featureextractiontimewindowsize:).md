

- Create ML
- MLSoundClassifier
- MLSoundClassifier.FeatureExtractionParameters
-  init(overlapFactor:featureExtractor:featureExtractionTimeWindowSize:) 

Initializer

# init(overlapFactor:featureExtractor:featureExtractionTimeWindowSize:)

Creates the parameters for a feature-extraction session.

iOS 15.0+iPadOS 15.0+Mac Catalyst 15.0+macOS 12.0+visionOS 1.0+

``` source
init(
    overlapFactor: Double = __Defaults.overlapFactor,
    featureExtractor: MLSoundClassifier.ModelParameters.FeatureExtractorType = __Defaults.featureExtractor,
    featureExtractionTimeWindowSize: TimeInterval?
)
```

## Parameters 

`overlapFactor`  

A portion of overlap between consecutive audio analysis windows. The value must be in the range `[0.0, 1.0)`.

`featureExtractor`  

An algorithm type the session uses to extract features from audio files.

`featureExtractionTimeWindowSize`  

A time duration, in seconds, the feature-extraction session uses for each audio sample it reads from an audio file in a dataset. The value must be in the range `[0.5, 15.0]`.

## See Also

### Creating feature extraction parameters

init(overlapFactor: Double, featureExtractor: MLSoundClassifier.ModelParameters.FeatureExtractorType)

Creates the parameters for a feature-extraction session with a default time window size.

