

- Create ML
- MLRandomForestClassifier
- MLRandomForestClassifier.ModelParameters
-  init(validationData:maxDepth:maxIterations:minLossReduction:minChildWeight:randomSeed:rowSubsample:columnSubsample:) Deprecated

Initializer

# init(validationData:maxDepth:maxIterations:minLossReduction:minChildWeight:randomSeed:rowSubsample:columnSubsample:)

Creates a new set of parameters.

iOS 15.0–16.0DeprecatediPadOS 15.0–16.0DeprecatedMac Catalyst 15.0–16.0DeprecatedmacOS 10.14–10.15DeprecatedvisionOS 1.0+

``` source
init(
    validationData: MLDataTable?,
    maxDepth: Int = 6,
    maxIterations: Int = 10,
    minLossReduction: Double = 0,
    minChildWeight: Double = 0.1,
    randomSeed: Int = 42,
    rowSubsample: Double = 0.8,
    columnSubsample: Double = 0.8
)
```

Deprecated

Use the validation property instead.

## Parameters 

`validationData`  

The dataset used to monitor how well the model is generalizing.

The default value is `nil` which will use an automatically sampled validation set.

`maxDepth`  

The maximum depth of the tree. Must be a value of at least 1.

The default value is 6.

`maxIterations`  

The maximum number of passes through the data.

The default value is 10.

`minLossReduction`  

The minimum amount of reduction in the loss function that is required to make another split to the data. Larger values help prevent overfitting.

The default value is 0.

`minChildWeight`  

Determines the minimum weight of each leaf node of the tree. Larger values help prevent overfitting.

The default value is 0.1.

`randomSeed`  

A seed for internal random operations. Set this value to ensure reproducible results.

The default value is 42.

`rowSubsample`  

Select the specified ratio from the training set to grow each tree. This technique is known as bagging.

The default value is 0.8.

`columnSubsample`  

Select the specified ratio of columns from the training set to use when growing each tree. Similar to row subsampling, this can be used to prevent overfitting.

The default value is 0.8

## See Also

### Creating parameters

init(validation: MLRandomForestClassifier.ModelParameters.ValidationData, maxDepth: Int, maxIterations: Int, minLossReduction: Double, minChildWeight: Double, randomSeed: Int, rowSubsample: Double, columnSubsample: Double)

enum ValidationData

Values for specifying validation data.

