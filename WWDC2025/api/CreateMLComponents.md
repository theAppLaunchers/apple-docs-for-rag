Framework

# Create ML Components

Create more customizable machine learning models in your app.

iOS 16.0+iPadOS 16.0+Mac Catalyst 16.0+macOS 13.0+tvOS 16.0+visionOS 1.0+watchOS 11.0+

## [Overview](/documentation/CreateMLComponents#Overview)

Create ML Components is a fundamental technology that exposes the underpinnings of monolithic tasks. You’re in full control and can create custom pipelines for greater flexibility.

![A flowchart that depicts a task represented as 4 component rectangles. The flow begins in the bottom left rectangle which has a camera icon to represent an input image and a label that reads Component 0. This rectangle has two flow arrows — one points up to the single rectangle above the other three rectangles. This top rectangle has a wand and four stars icon that represents an enhancement to the image and a label that reads Component 1. The second flow arrow points to the bottom center rectangle which has a screen within a screen scaling icon that represents the resizing of the image and a label that reads Component 2. Next, the single top rectangle has a flow arrow that points down to the bottom right rectangle which has a photo icon that represents the finished image and a label that reads Component n. A series of three dots connects this rectangle to the center rectangle in the bottom row.](https://docs-assets.developer.apple.com/published/eb40070181caf3b058aa089ccb01534f/%402xcreate-ml-task.png)

Use components to configure your machine learning tasks with a detailed level of granularity. Choose a specific classifier for images, video, or tabular data.

## [Topics](/documentation/CreateMLComponents#topics)

### [Image components](/documentation/CreateMLComponents#Image-components)

[

Augmenting images to expand your training data](/documentation/createmlcomponents/augmenting-images-to-expand-your-training-data)

Improve your model by using transformed versions of your training images.

[

Creating a multi-label image classifier](/documentation/createmlcomponents/creating-a-multi-label-image-classifier)

Train a machine learning model to assign multiple labels to an image.

```swift
```swift
```swift
struct ImageReader
```
```

An image file reader.
```
```swift
```swift
```swift
protocol ImageFeatureExtractor
```
```

A transformer that takes an image and outputs image features.
```
```swift
```swift
```swift
struct ImageCropper
```
```

An image crop transformer.
```
```swift
```swift
```swift
struct ImageScaler
```
```

An image scaling transformer.
```
```swift
```swift
```swift
struct ImageFeaturePrint
```
```

ImageFeaturePrint image feature extractor.
```
```swift
```swift
```swift
struct ImageBlur
```
```

An image blurring transformer.
```
```swift
```swift
```swift
struct ImageColorTransformer
```
```

An image color transformer.
```
```swift
```swift
```swift
struct ImageExposureAdjuster
```
```

An image exposure adjusting transformer.
```
```swift
```swift
```swift
struct ImageFlipper
```
```

An image flipper transformer.
```
```swift
```swift
```swift
struct ImageRotator
```
```

An image rotating transformer.
```
```swift
```swift
```swift
struct RandomImageNoiseGenerator
```
```

A transformer that adds random noise to an image.
```
```swift
```swift
```swift
struct MLModelImageFeatureExtractor
```
```

An image feature extractor provided by an MLModel.
```

### [Pose components](/documentation/CreateMLComponents#Pose-components)

[

Counting human body action repetitions in a live video feed](/documentation/createmlcomponents/counting_human_body_action_repetitions_in_a_live_video_feed)

Use Create ML Components to analyze a series of video frames and count a person’s repetitive or periodic body movements.

```swift
```swift
```swift
struct Pose
```
```

A pose that contains joint keypoints from a person, a hand, or a combination.
```
```swift
```swift
```swift
struct JointKey
```
```

A key that uniquely identifies a joint.
```
```swift
```swift
```swift
struct JointPoint
```
```

A joint in a pose that contains a location and scoring information.
```
```swift
```swift
```swift
struct PoseSelector
```
```

A transformer that selects one pose from an array of poses.
```
```swift
```swift
```swift
enum PoseSelectionStrategy
```
```

Pose selection strategy.
```
```swift
```swift
```swift
struct JointsSelector
```
```

Joints selector from a pose.
```
```swift
```swift
```swift
struct HumanBodyPoseExtractor
```
```

The human body pose image feature extractor.
```
```swift
```swift
```swift
struct HumanHandPoseExtractor
```
```

The human hand pose image feature extractor.
```
```swift
```swift
```swift
struct HumanBodyActionCounter
```
```

A human body action repetition counting transformer that takes window of human body poses and produces cumulative human body action repetition counts.
```
```swift
```swift
```swift
struct HumanBodyActionPeriodPredictor
```
```

A human body action period predictor transformer that takes window of poses and produces a window of predictions.
```

### [Audio components](/documentation/CreateMLComponents#Audio-components)

```swift
```swift
```swift
```swift
struct AudioReader
```
```

An audio file reader.
```
```swift
```swift
```swift
struct AudioFeaturePrint
```
```

A stream transformer that extracts audio features from audio buffers.
```
```swift
```swift
```swift
struct AudioConvertingTransformer
```
```

A transformer for audio conversion.
```
```

### [Time-based components](/documentation/CreateMLComponents#Time-based-components)

[

Creating a time-series classifier](/documentation/createmlcomponents/creating-a-time-series-classifier)

Train a machine learning model to predict the class label of time-series signals.

[

Creating a time-series forecaster](/documentation/createmlcomponents/creating-a-time-series-forecaster)

Forecast future data points by training a machine learning model using historical data.

```swift
```swift
```swift
struct DateFeatures
```
```

A set of date and time features.
```
```swift
```swift
```swift
struct DateFeatureExtractor
```
```

A time and date feature extractor.
```
```swift
```swift
```swift
struct LinearTimeSeriesForecaster
```
```

A time-series forecasting estimator.
```
```swift
```swift
```swift
struct LinearTimeSeriesForecasterConfiguration
```
```

The configuration for a linear time-series forecaster.
```
```swift
```swift
```swift
struct TimeSeriesForecasterBatches
```
```

A sequence of forecaster batches on a time series shaped array.
```
```swift
```swift
```swift
struct TimeSeriesForecasterAnnotatedWindows
```
```

A sequence of forecasting windows on a time series shaped array.
```
```swift
```swift
```swift
struct TemporalFeature
```
```

A temporal feature contains a segment identifier and a feature value.
```
```swift
```swift
```swift
protocol TemporalSequence
```
```

Async sequence for temporal features.
```
```swift
```swift
```swift
struct TemporalSegmentIdentifier
```
```

Uniquely identifiers a segment of a temporal sequence.
```
```swift
```swift
```swift
struct SlidingWindows
```
```

A sequence of windows on a time series shaped array.
```
```swift
```swift
```swift
struct SlidingWindowTransformer
```
```

A temporal transformer that groups input elements.
```
```swift
```swift
```swift
struct Downsampler
```
```

A temporal transformer that down samples the input stream.
```
```swift
```swift
```swift
struct VideoReader
```
```

A video file reader.
```
```swift
```swift
```swift
struct TemporalFileSegment
```
```

A URL and a time range identifying a specific segment of a time-based (temporal) file.
```
```swift
```swift
```swift
struct AnyTemporalIterator
```
```

A type-erased async iterator.
```
```swift
```swift
```swift
struct AnyTemporalSequence
```
```

A type-erased temporal sequence.
```
```swift
```swift
```swift
struct PreprocessedFeatureSequence
```
```

An asynchronous sequence of eagerly stored temporal features.
```

### [Object detection components](/documentation/CreateMLComponents#Object-detection-components)

```swift
```swift
```swift
```swift
struct DetectedObject
```
```

An item in a detection result.
```
```swift
```swift
```swift
struct ObjectDetectionAnnotation
```
```

An object detection annotation.
```
```swift
```swift
```swift
struct ObjectDetectionMetrics
```
```

Metrics for object detection model.
```
```

### [Tabular components](/documentation/CreateMLComponents#Tabular-components)

```swift
```swift
```swift
```swift
protocol TabularTransformer
```
```

A tabular transformer that transforms a data frame.
```
```swift
```swift
```swift
protocol TabularEstimator
```
```

A tabular estimator that creates a transformer by fitting to a data set in a data frame.
```
```swift
```swift
```swift
protocol SupervisedTabularEstimator
```
```

A tabular estimator that creates a transformer by fitting to a data set in a data frame.
```
```swift
```swift
```swift
struct ColumnSelector
```
```

An operation that applies an estimator to a selection of columns.
```
```swift
```swift
```swift
struct ColumnSelectorTransformer
```
```

A transformer that applies a base transformer to specific columns in a data frame.
```
```swift
```swift
```swift
enum ColumnSelection
```
```

A selection of columns from a data frame.
```
```swift
```swift
```swift
struct ColumnConcatenator
```
```

A transformer that concatenates every numerical column in a dataframe into to a shaped array for each row.
```
```swift
```swift
```swift
struct PreprocessingSupervisedTabularEstimator
```
```

A supervised tabular estimator that composes a preprocessing transformer and a supervised tabular estimator.
```
```swift
```swift
```swift
struct PreprocessingTabularEstimator
```
```

An estimator that composes a preprocessing transformer and an estimator.
```
```swift
```swift
```swift
struct PreprocessingUpdatableSupervisedTabularEstimator
```
```

An updatable supervised estimator that composes a preprocessing transformer and an updatable supervised estimator.
```
```swift
```swift
```swift
struct PreprocessingUpdatableTabularEstimator
```
```

An updatable estimator that composes a preprocessing transformer and an updatable estimator.
```
```

### [Protocols](/documentation/CreateMLComponents#Protocols)

```swift
```swift
```swift
```swift
protocol Transformer
```
```

A transformer that takes an input and produces an output.
```
```swift
```swift
```swift
protocol TemporalTransformer
```
```

A transformer that takes an asynchronous input sequence of temporal features and produces an asynchronous output sequence.
```
```swift
```swift
```swift
protocol RandomTransformer
```
```

A transformer that takes an input and a random number generator and produces a randomized output.
```
```swift
```swift
```swift
protocol Estimator
```
```

An estimator that creates a transformer by fitting to a data set.
```
```swift
```swift
```swift
protocol TemporalEstimator
```
```

An estimator that creates a transformer by fitting to a sequence of temporal features.

Deprecated
```
```swift
```swift
```swift
protocol SupervisedEstimator
```
```

An estimator that creates a transformer by fitting to a data set.
```
```swift
```swift
```swift
protocol SupervisedTemporalEstimator
```
```

An estimator that creates a transformer by fitting to a sequence of annotated temporal features.

Deprecated
```
```swift
```swift
```swift
protocol UpdatableEstimator
```
```

An estimator that can be incrementally updated.
```
```swift
```swift
```swift
protocol UpdatableSupervisedEstimator
```
```

A supervised estimator that can be incrementally updated.
```
```swift
```swift
```swift
protocol UpdatableSupervisedTemporalEstimator
```
```

A supervised temporal estimator that can be incrementally updated.

Deprecated
```
```swift
```swift
```swift
protocol UpdatableSupervisedTabularEstimator
```
```

A supervised tabular estimator that can be incrementally updated.
```
```swift
```swift
```swift
protocol UpdatableTemporalEstimator
```
```

A temporal estimator that can be incrementally updated.

Deprecated
```
```swift
```swift
```swift
protocol UpdatableTabularEstimator
```
```

A tabular estimator that can be incrementally updated.
```
```

### [Core ML adaptors](/documentation/CreateMLComponents#Core-ML-adaptors)

```swift
```swift
```swift
```swift
struct MLModelTransformerAdaptor
```
```

A transformer that uses a Core ML model.
```
```swift
```swift
```swift
struct MLModelClassifierAdaptor
```
```

A transformer that uses a Core ML model as a classifier.
```
```swift
```swift
```swift
struct MLModelRegressorAdaptor
```
```

A transformer that uses a Core ML model as a regressor.
```
```swift
```swift
```swift
struct ModelMetadata
```
```

User info keys that specify useful information about a model.
```
```

### [Annotations](/documentation/CreateMLComponents#Annotations)

```swift
```swift
```swift
```swift
struct AnnotatedFiles
```
```

An annotated files collection.
```
```swift
```swift
```swift
struct AnnotatedBatch
```
```

A batch of annotated examples for fitting a supervised estimator.
```
```swift
```swift
```swift
struct AnnotatedFeature
```
```

An annotated example for fitting a supervised estimator.
```
```swift
```swift
```swift
struct AnnotatedFeatureProvider
```
```

An adaptor that converts a regular estimator to a tabular estimator by selecting features and annotations from columns.
```
```swift
```swift
```swift
struct AnnotatedPrediction
```
```

An annotated prediction.
```
```swift
```swift
```swift
struct DataFrameTemporalAnnotationParameters
```
```

Annotation parameters for the dataframe containing temporal annotations.
```
```

### [Augmentations](/documentation/CreateMLComponents#Augmentations)

```swift
```swift
```swift
```swift
struct ApplyEachRandomly
```
```

Applies each transformer randomly given a probability.
```
```swift
```swift
```swift
struct ApplyRandomly
```
```

Randomly applies the transformer with the given probability.
```
```swift
```swift
```swift
struct AugmentationBuilder
```
```

A series of augmentations.
```
```swift
```swift
```swift
struct AugmentationSequence
```
```

An async sequence of augmented elements.
```
```swift
```swift
```swift
struct Augmenter
```
```

An augmenter.
```
```swift
```swift
```swift
struct ChooseRandomly
```
```

Apply single transformation randomly chosen from a list of transformers.
```
```swift
```swift
```swift
struct RandomImageCropper
```
```

Crops an image at a random location.
```
```swift
```swift
```swift
struct ShuffleRandomly
```
```

Apply transformations in a random order.
```
```swift
```swift
```swift
struct UniformRandomFloatingPointParameter
```
```

Applies the transformer with a randomly generated input parameter.
```
```swift
```swift
```swift
class UniformRandomIntegerParameter
```
```

Applies the transformer with a randomly generated input parameter.
```
```swift
```swift
```swift
struct UpsampledAugmentationSequence
```
```

An async sequence of augmented elements.
```
```

### [Event handling](/documentation/CreateMLComponents#Event-handling)

```swift
```swift
```swift
```swift
struct Event
```
```

Maintains the status of the pipeline.
```
```swift
```swift
```swift
typealias EventHandler
```
```

A closure to handle processing events.
```
```swift
```swift
```swift
struct MetricsKey
```
```

A key that uniquely identifies a metric.
```
```

### [Scalers](/documentation/CreateMLComponents#Scalers)

```swift
```swift
```swift
```swift
struct StandardScaler
```
```

An estimator that standardizes the input by removing the mean and scaling to unit variance.
```
```swift
```swift
```swift
struct MaxAbsScaler
```
```

An estimator that scales the input values so that the maximum absolute value is 1.0.
```
```swift
```swift
```swift
struct MinMaxScaler
```
```

An estimator that scales the input values so that they all lie in a closed range.
```
```swift
```swift
```swift
struct NormalizationScaler
```
```

An estimator that normalizes the input values using a normalization strategy.
```
```swift
```swift
```swift
struct RobustScaler
```
```

An estimator that scales the input using statistics that are robust to outliers.
```
```

### [Preprocessors](/documentation/CreateMLComponents#Preprocessors)

```swift
```swift
```swift
```swift
struct LinearTransformer
```
```

A transformer that runs an input through a scale and offset.
```
```swift
```swift
```swift
struct ImputeTransformer
```
```

A transformer that replaces missing values with a pre-defined value.
```
```swift
```swift
```swift
struct OneHotEncoder
```
```

An estimator that encodes categorical values to an integer array.
```
```swift
```swift
```swift
struct OrdinalEncoder
```
```

An ordinal encoder estimator encodes categorical values to ordinal integer values.
```
```swift
```swift
```swift
struct NumericImputer
```
```

An estimator that replaces missing values in the numeric input.
```
```swift
```swift
```swift
struct Reshaper
```
```

A transformer that reshapes a shaped array.
```
```swift
```swift
```swift
struct CategoricalImputer
```
```

An estimator that replaces missing values in the categorical input.
```
```swift
```swift
```swift
struct OptionalUnwrapper
```
```

A transformer that unwraps optional elements and throws when encountering missing values.
```
```

### [Regressors](/documentation/CreateMLComponents#Regressors)

```swift
```swift
```swift
```swift
protocol Regressor
```
```

A transformer that predicts a float value.
```
```swift
```swift
```swift
struct LinearRegressor
```
```

A linear regressor.
```
```swift
```swift
```swift
struct LinearRegressorModel
```
```

A trained linear regressor model.
```
```swift
```swift
```swift
struct MultivariateLinearRegressor
```
```

A multivariate linear regressor.
```
```swift
```swift
```swift
struct MultivariateLinearRegressorConfiguration
```
```

A linear regressor configuration.
```
```swift
```swift
```swift
struct Model
```
```

A trained multivariate linear regressor model.
```
```swift
```swift
```swift
struct FullyConnectedNetworkRegressor
```
```

A regressor that uses a fully connected network.
```
```swift
```swift
```swift
struct FullyConnectedNetworkRegressorModel
```
```

A regressor model that uses a fully connected network.
```
```swift
```swift
```swift
struct BoostedTreeRegressor
```
```

A gradient boosted decision tree regressor.
```
```swift
```swift
```swift
struct TreeRegressorModel
```
```

A trained tree regressor model.
```
```swift
```swift
```swift
enum OptimizationStrategy
```
```

A linear optimization strategy.
```
```

### [Serializers](/documentation/CreateMLComponents#Serializers)

```swift
```swift
```swift
```swift
protocol EstimatorDecoder
```
```

A type that can decode values from a model representation.
```
```swift
```swift
```swift
protocol EstimatorEncoder
```
```

A type that can encode values into a model representation.
```
```

### [Classifiers](/documentation/CreateMLComponents#Classifiers)

```swift
```swift
```swift
```swift
protocol Classifier
```
```

An estimator that predicts classification probabilities.
```
```swift
```swift
```swift
struct LogisticRegressionClassifier
```
```

A logistic regression classifier.
```
```swift
```swift
```swift
struct LogisticRegressionClassifierModel
```
```

A trained logistic regression classifier model.
```
```swift
```swift
```swift
struct BoostedTreeClassifier
```
```

A gradient boosted decision tree classifier.
```
```swift
```swift
```swift
struct BoostedTreeConfiguration
```
```

A boosted tree configuration.
```
```swift
```swift
```swift
struct FullyConnectedNetworkClassifier
```
```

A classifier that uses a fully connected network.
```
```swift
```swift
```swift
struct FullyConnectedNetworkClassifierModel
```
```

A classifier model that uses a fully connected network.
```
```swift
```swift
```swift
struct FullyConnectedNetworkMultiLabelClassifier
```
```

A classifier that uses a multi-label fully-connected network.
```
```swift
```swift
```swift
struct FullyConnectedNetworkMultiLabelClassifierModel
```
```

A multi-label classifier model that uses a fully-connected network.
```
```swift
```swift
```swift
struct FullyConnectedNetworkConfiguration
```
```

A fully connected network configuration.
```
```swift
```swift
```swift
struct TreeClassifierModel
```
```

A trained tree classifier model.
```
```swift
```swift
```swift
struct TimeSeriesClassifier
```
```
```
```swift
```swift
```swift
struct TimeSeriesClassifierConfiguration
```
```

The configuration for a time-series classifier.
```
```

### [Metrics](/documentation/CreateMLComponents#Metrics)

```swift
```swift
```swift
```swift
struct Classification
```
```

An item in a classification result.
```
```swift
```swift
```swift
struct ClassificationDistribution
```
```

A classification distribution that contains a probability for each classification label.
```
```swift
```swift
```swift
struct ClassificationMetrics
```
```

Classification metrics.
```
```swift
```swift
```swift
struct MultiLabelClassificationMetrics
```
```

Multi-label classification metrics.
```
```swift
```swift
```swift
func rootMeanSquaredError<T>([AnnotatedPrediction<T, T>]) -> T
```
```

Computes the root mean squared error between predicted and ground truth values.
```
```swift
```swift
```swift
func rootMeanSquaredError<T>(some Collection, some Collection) -> T
```
```

Computes the root mean squared error between predicted and ground truth values.
```
```swift
```swift
```swift
func maximumAbsoluteError<T>([AnnotatedPrediction<T, T>]) -> T
```
```

Computes the maximum absolute error between predicted and ground truth values.
```
```swift
```swift
```swift
func maximumAbsoluteError<T>(some Collection, some Collection) -> T
```
```

Computes the maximum absolute error between predicted and ground truth values.
```
```swift
```swift
```swift
func meanAbsoluteError<T>([AnnotatedPrediction<T, T>]) -> T
```
```

Computes the mean absolute error between predicted and ground truth values.
```
```swift
```swift
```swift
func meanAbsoluteError<T>(some Collection, some Collection) -> T
```
```

Computes the mean absolute error between predicted and ground truth values.
```
```swift
```swift
```swift
func meanAbsolutePercentageError<T>([AnnotatedPrediction<T, T>]) -> T
```
```

Computes the mean absolute percentage error between predicted and ground truth values.
```
```swift
```swift
```swift
func meanSquaredError<T>([AnnotatedPrediction<T, T>]) -> T
```
```

Computes the root mean squared error between predicted and ground truth values.
```
```swift
```swift
```swift
func meanSquaredError<T>(some Collection, some Collection) -> T
```
```

Computes the mean squared error between predicted and ground truth values.
```
```

### [Transformer adaptors](/documentation/CreateMLComponents#Transformer-adaptors)

```swift
```swift
```swift
```swift
struct TransformerToEstimatorAdaptor
```
```

An estimator that always returns a predefined transformer.
```
```swift
```swift
```swift
struct TransformerToTemporalAdaptor
```
```

A temporal transformer that applies a regular transformer to each value of a temporal sequence.

Deprecated
```
```swift
```swift
```swift
struct TransformerToUpdatableEstimatorAdaptor
```
```

An updatable estimator that always returns a predefined transformer.
```
```

### [Updatable adaptors](/documentation/CreateMLComponents#Updatable-adaptors)

```swift
```swift
```swift
```swift
struct UpdatableEstimatorToTemporalAdaptor
```
```

An updatable temporal estimator wrapping an updatable estimator.

Deprecated
```
```swift
```swift
```swift
struct UpdatableEstimatorToSupervisedAdaptor
```
```

An adaptor that exposes an updatable estimator as an updatable supervised estimator.
```
```swift
```swift
```swift
struct UpdatableSupervisedEstimatorToTemporalAdaptor
```
```

An updatable supervised temporal estimator wrapping an updatable supervised estimator.

Deprecated
```
```swift
```swift
```swift
struct UpdatableTemporalEstimatorToSupervisedAdaptor
```
```

An adaptor that exposes an updatable temporal estimator as an updatable supervised temporal estimator.

Deprecated
```
```

### [Estimator adaptors](/documentation/CreateMLComponents#Estimator-adaptors)

```swift
```swift
```swift
```swift
struct EstimatorToSupervisedAdaptor
```
```

An adaptor that exposes an estimator as a supervised estimator.
```
```swift
```swift
```swift
struct EstimatorToTemporalAdaptor
```
```

A temporal estimator wrapping an estimator.

Deprecated
```
```swift
```swift
```swift
struct SupervisedEstimatorToTemporalAdaptor
```
```

A supervised temporal estimator wrapping a supervised estimator.

Deprecated
```
```

### [Tabular adaptors](/documentation/CreateMLComponents#Tabular-adaptors)

```swift
```swift
```swift
```swift
struct TabularEstimatorToSupervisedAdaptor
```
```

An adaptor that exposes a tabular estimator as a tabular supervised estimator.
```
```swift
```swift
```swift
struct TabularTransformerToEstimatorAdaptor
```
```

A tabular estimator that always returns a predefined tabular transformer.
```
```swift
```swift
```swift
struct TabularTransformerToUpdatableEstimatorAdaptor
```
```

An updatable tabular estimator that always returns a predefined transformer.
```
```swift
```swift
```swift
struct UpdatableTabularEstimatorToSupervisedAdaptor
```
```

An adaptor that exposes an updatable tabular estimator as an updatable supervised tabular estimator.
```
```

### [Temporal adaptors](/documentation/CreateMLComponents#Temporal-adaptors)

```swift
```swift
```swift
```swift
struct TemporalAdaptor
```
```

A temporal transformer that applies a regular transformer to each value of a temporal sequence.
```
```swift
```swift
```swift
struct TemporalTransformerToEstimatorAdaptor
```
```

A temporal estimator that always returns a predefined temporal transformer.

Deprecated
```
```swift
```swift
```swift
struct TemporalEstimatorToSupervisedAdaptor
```
```

An adaptor that exposes a temporal estimator as a supervised temporal estimator.

Deprecated
```
```swift
```swift
```swift
struct TemporalTransformerToUpdatableEstimatorAdaptor
```
```

A temporal estimator that always returns a predefined temporal transformer.

Deprecated
```
```

### [Composition with preprocessing](/documentation/CreateMLComponents#Composition-with-preprocessing)

```swift
```swift
```swift
```swift
struct PreprocessingEstimator
```
```

An estimator that composes a preprocessing transformer and an estimator.
```
```swift
```swift
```swift
struct PreprocessingTemporalEstimator
```
```

A temporal estimator that composes a preprocessing transformer and a temporal estimator.

Deprecated
```
```swift
```swift
```swift
struct PreprocessingSupervisedEstimator
```
```

A supervised estimator that composes a preprocessing transformer and a supervised estimator.
```
```swift
```swift
```swift
struct PreprocessingSupervisedTemporalEstimator
```
```

A supervised temporal estimator that composes a preprocessing transformer and a supervised temporal estimator.

Deprecated
```
```swift
```swift
```swift
struct PreprocessingUpdatableEstimator
```
```

An updatable estimator that composes a preprocessing transformer and an updatable estimator.
```
```swift
```swift
```swift
struct PreprocessingUpdatableTemporalEstimator
```
```

An updatable temporal estimator that composes a preprocessing transformer and an updatable temporal estimator.

Deprecated
```
```swift
```swift
```swift
struct PreprocessingUpdatableSupervisedEstimator
```
```

An updatable supervised estimator that composes a preprocessing transformer and an updatable supervised estimator.
```
```swift
```swift
```swift
struct PreprocessingUpdatableSupervisedTemporalEstimator
```
```

An updatable supervised temporal estimator that composes a preprocessing transformer and an updatable supervised temporal estimator.

Deprecated
```
```

### [Composition](/documentation/CreateMLComponents#Composition)

```swift
```swift
```swift
```swift
struct ComposedTransformer
```
```

A transformer that composes two transformers by applying them one after the other.
```
```swift
```swift
```swift
struct ComposedTemporalTransformer
```
```

A temporal transformer that composes two temporal transformers by applying them one after the other.
```
```swift
```swift
```swift
struct ComposedTabularTransformer
```
```

A transformer that composes two tabular transformers by applying them one after the other.
```
```

### [Errors](/documentation/CreateMLComponents#Errors)

```swift
```swift
```swift
```swift
enum AudioPreprocessingError
```
```

Audio preprocessing errors.
```
```swift
```swift
```swift
enum AudioReaderError
```
```

Audio reader errors.
```
```swift
```swift
```swift
enum CompatibilityError
```
```

A compatibility error.
```
```swift
```swift
```swift
enum ConcatenationError
```
```

Errors thrown when concatenating numeric values.
```
```swift
```swift
```swift
enum DatasetError
```
```

Dataset processing errors.
```
```swift
```swift
```swift
enum EstimatorEncodingError
```
```

An estimator encoding error.
```
```swift
```swift
```swift
enum ModelCompatibilityError
```
```

Errors related to CoreML model compatibility.
```
```swift
```swift
```swift
enum ModelUpdateError
```
```

An updatable model error.
```
```swift
```swift
```swift
enum OptimizationError
```
```

An optimization error.
```
```swift
```swift
```swift
enum PipelineDataError
```
```

Errors related to pipeline data affinity problems.
```
```swift
```swift
```swift
enum SerializationError
```
```

A serialization error.
```
```swift
```swift
```swift
enum TabularPipelineDataError
```
```

Errors related to tabular pipeline data affinity problems.
```
```swift
```swift
```swift
enum VideoReaderError
```
```

Video loader errors.
```
```