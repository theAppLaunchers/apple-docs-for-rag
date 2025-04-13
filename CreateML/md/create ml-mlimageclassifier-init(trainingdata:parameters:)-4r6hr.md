

- Create ML
- MLImageClassifier
-  init(trainingData:parameters:) 

Initializer

# init(trainingData:parameters:)

Creates an image classifier with a training dataset represented by a data source.

iOS 15.0+iPadOS 15.0+Mac Catalyst 15.0+macOS 11.0+visionOS 1.0+

``` source
init(
    trainingData: MLImageClassifier.DataSource,
    parameters: MLImageClassifier.ModelParameters = ModelParameters(
            validation: .split(strategy: .automatic),
            augmentation: [],
            algorithm: .transferLearning(
                featureExtractor: .scenePrint(revision: 1),
                classifier: .logisticRegressor
            )
        )
) throws
```

## Parameters 

`trainingData`  

A set of labeled images the task uses to train the image classifier model, contained in a data source.

`parameters`  

An MLImageClassifier.ModelParameters instance you use to configure the model for the training session.

## Mentioned in 

Creating an Image Classifier Model

## Discussion

When you create an MLImageClassifier instance, initialize it with an MLImageClassifier.ModelParameters structure. This allows you to configure the image classifier training process. For example, you can explicitly define the validation dataset instead of allowing the model to choose a random selection of your training data. Alternatively, as shown in the following example, set `validationData` to `nil` to allow the classifier to choose the validation data for you from among your training data. This lets you set other parameters—like maximum iterations and augmentation options—to values other than the default.

```
let parameters = MLImageClassifier.ModelParameters(
    featureExtractor: .scenePrint(revision: 1),
    validationData: nil,
    maxIterations: 20,
    augmentationOptions: [.crop]
)
```

Use the parameter structure and your training data to build a classifier. The following example uses training data from labeled directories within a directory called `Training`, which resides in the `Downloads` directory:

```
if let downloads = FileManager.default.urls(for: .downloadsDirectory, in: .userDomainMask).first {
    let trainingURL = downloads.appendingPathComponent("Training")
    let classifier = try MLImageClassifier(
        trainingData: .labeledDirectories(at: trainingURL),
        parameters: parameters
    )
}
```

Training begins immediately.

Note

If you represent your training data with a dictionary of strings and corresponding URL arrays, use init(trainingData:parameters:) instead.

## See Also

### Training an image classifier synchronously

init(trainingData: [String : [URL]], parameters: MLImageClassifier.ModelParameters) throws

Creates an image classifier with a training dataset represented by a dictionary.

Deprecated

