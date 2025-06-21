Framework

# Core ML

Integrate machine learning models into your app.

iOS 11.0+iPadOS 11.0+Mac Catalyst 13.0+macOS 10.13+tvOS 11.0+visionOS 1.0+watchOS 4.0+

## [Overview](/documentation/CoreML#overview)

Use [Core ML](/documentation/coreml) to integrate machine learning models into your app. [Core ML](/documentation/coreml) provides a unified representation for all models. Your app uses [Core ML](/documentation/coreml) APIs and user data to make predictions, and to train or fine-tune models, all on a person’s device.

![Flow diagram going from left to right. Starting on the left is a Core ML model file icon. Next, in the center is the Core ML framework icon, and on the right is a generic app icon, labeled “your app”.](https://docs-assets.developer.apple.com/published/ae17ffa70ecbce075dc4b57539ec6dde/media-3901331%402x.png)

A model is the result of applying a machine learning algorithm to a set of training data. You use a model to make predictions based on new input data. Models can accomplish a wide variety of tasks that would be difficult or impractical to write in code. For example, you can train a model to categorize photos, or detect specific objects within a photo directly from its pixels.

You build and train a model with the [Create ML app](https://developer.apple.com/machine-learning/create-ml/) bundled with Xcode. Models trained using [Create ML](/documentation/CreateML) are in the [Core ML](/documentation/coreml) model format and are ready to use in your app. Alternatively, you can use a wide variety of other machine learning libraries and then use [Core ML Tools](https://coremltools.readme.io) to convert the model into the [Core ML](/documentation/coreml) format. Once a model is on a person’s device, you can use [Core ML](/documentation/coreml) to retrain or fine-tune it on-device, with that person’s data.

[Core ML](/documentation/coreml) optimizes on-device performance by leveraging the CPU, GPU, and Neural Engine while minimizing its memory footprint and power consumption. Running a model strictly on a person’s device removes any need for a network connection, which helps keep a person’s data private and your app responsive.

The framework is the foundation for domain-specific frameworks and functionality. It supports [Vision](/documentation/Vision) for analyzing images, [Natural Language](/documentation/NaturalLanguage) for processing text, [Speech](/documentation/Speech) for converting audio to text, and [Sound Analysis](/documentation/SoundAnalysis) for identifying sounds in audio. [Core ML](/documentation/coreml) itself builds on top of low-level primitives like [Accelerate](/documentation/Accelerate) and [`BNNS`](/documentation/Accelerate/BNNS), as well as [Metal Performance Shaders](/documentation/metalperformanceshaders).

![A block diagram of the machine learning stack. The top layer is a single block labeled “Your app,” which spans the entire width of the block diagram. The second layer has four blocks labeled “Vision,” “Natural Language,” “Speech,” and “Sound Analysis.” The third layer is labeled “Core ML,” which also spans the entire width. The fourth and final layer has two blocks, “Accelerate and BNNS” and “Metal Performance Shaders.”](https://docs-assets.developer.apple.com/published/2ab0327b082af0332b528cc4171ee629/media-3330367%402x.png)

## [Topics](/documentation/CoreML#topics)

### [Core ML models](/documentation/CoreML#Core-ML-models)

[

Getting a Core ML Model](/documentation/coreml/getting-a-core-ml-model)

Obtain a Core ML model to use in your app.

[

Updating a Model File to a Model Package](/documentation/coreml/updating-a-model-file-to-a-model-package)

Convert a Core ML model file into a model package in Xcode.

[

Integrating a Core ML Model into Your App](/documentation/coreml/integrating-a-core-ml-model-into-your-app)

Add a simple model to an app, pass input data to the model, and process the model’s predictions.

```swift
```swift
```swift
class MLModel
```
```

An encapsulation of all the details of your machine learning model.
```

[

API Reference

Model Customization](/documentation/coreml/model-customization)

Expand and modify your model with new layers.

[

API Reference

Model Personalization](/documentation/coreml/model-personalization)

Update your model to adapt to new data.

### [Model inputs and outputs](/documentation/CoreML#Model-inputs-and-outputs)

[

Making Predictions with a Sequence of Inputs](/documentation/coreml/making-predictions-with-a-sequence-of-inputs)

Integrate a recurrent neural network model to process sequences of inputs.

```swift
```swift
```swift
class MLFeatureValue
```
```

A generic wrapper around an underlying value and the value’s type.
```
```swift
```swift
```swift
struct MLSendableFeatureValue
```
```

A sendable feature value.
```
```swift
```swift
```swift
protocol MLFeatureProvider
```
```

An interface that represents a collection of values for either a model’s input or its output.
```
```swift
```swift
```swift
class MLDictionaryFeatureProvider
```
```

A convenience wrapper for the given dictionary of data.
```
```swift
```swift
```swift
protocol MLBatchProvider
```
```

An interface that represents a collection of feature providers.
```
```swift
```swift
```swift
class MLArrayBatchProvider
```
```

A convenience wrapper for batches of feature providers.
```
```swift
```swift
```swift
class MLModelAsset
```
```

An abstraction of a compiled Core ML model asset.
```

### [App integration](/documentation/CoreML#App-integration)

[

Downloading and Compiling a Model on the User’s Device](/documentation/coreml/downloading-and-compiling-a-model-on-the-user-s-device)

Install Core ML models on the user’s device dynamically at runtime.

[

API Reference

Model Integration Samples](/documentation/coreml/model-integration-samples)

Integrate tabular, image, and text classifcation models into your app.

### [Model encryption](/documentation/CoreML#Model-encryption)

[

Generating a Model Encryption Key](/documentation/coreml/generating-a-model-encryption-key)

Create a model encryption key to encrypt a compiled model or model archive.

[

Encrypting a Model in Your App](/documentation/coreml/encrypting-a-model-in-your-app)

Encrypt your app’s built-in model at compile time by adding a compiler flag.

### [Compute devices](/documentation/CoreML#Compute-devices)

```swift
```swift
```swift
```swift
enum MLComputeDevice
```
```

Compute devices for framework operations.
```
```swift
```swift
```swift
class MLCPUComputeDevice
```
```

An object that represents a CPU compute device.
```
```swift
```swift
```swift
class MLGPUComputeDevice
```
```

An object that represents a GPU compute device.
```
```swift
```swift
```swift
class MLNeuralEngineComputeDevice
```
```

An object that represents a Neural Engine compute device.
```
```swift
```swift
```swift
protocol MLComputeDeviceProtocol
```
```

An interface that represents a compute device type.
```
```

### [Compute plan](/documentation/CoreML#Compute-plan)

```swift
```swift
```swift
```swift
class MLComputePlan
```
```

A class representing the compute plan of a model.
```
```swift
```swift
```swift
enum MLModelStructure
```
```

An enum representing the structure of a model.
```
```swift
```swift
```swift
struct MLComputePolicy
```
```

The compute policy determining what compute device, or compute devices, to execute ML workloads on.
```
```swift
```swift
```swift
func withMLTensorComputePolicy<R>(MLComputePolicy, () async throws -> R) async rethrows -> R
```
```

Calls the given closure within a task-local context using the specified compute policy to influence what compute device tensor operations are executed on.
```
```swift
```swift
```swift
func withMLTensorComputePolicy<Result>(MLComputePolicy, () throws -> Result) rethrows -> Result
```
```

Calls the given closure within a task-local context using the specified compute policy to influence what compute device tensor operations are executed on.
```
```

### [Model state](/documentation/CoreML#Model-state)

```swift
```swift
```swift
```swift
class MLState
```
```

Handle to the state buffers.
```
```swift
```swift
```swift
class MLStateConstraint
```
```

Constraint of a state feature value.
```
```

### [Model tensor](/documentation/CoreML#Model-tensor)

```swift
```swift
```swift
```swift
struct MLTensor
```
```

A multi-dimensional array of numerical or Boolean scalars tailored to ML use cases, containing methods to perform transformations and mathematical operations efficiently using a ML compute device.
```
```swift
```swift
```swift
protocol MLTensorScalar
```
```

A type that represents the tensor scalar types supported by the framework. Don’t use this type directly.
```
```swift
```swift
```swift
protocol MLTensorRangeExpression
```
```

A type that can be used to slice a dimension of a tensor. Don’t use this type directly.
```
```

### [Model structure](/documentation/CoreML#Model-structure)

```swift
```swift
```swift
```swift
enum MLModelStructure
```
```

An enum representing the structure of a model.
```
```

### [Model errors](/documentation/CoreML#Model-errors)

```swift
```swift
```swift
```swift
struct MLModelError
```
```

Information about a Core ML model error.
```
```swift
```swift
```swift
enum Code
```
```

Information about a Core ML model error.
```
```swift
```swift
```swift
let MLModelErrorDomain: String
```
```

The domain for Core ML errors.
```
```

### [Model deployments](/documentation/CoreML#Model-deployments)

```swift
```swift
```swift
```swift
class MLModelCollection
```
```

A set of Core ML models from a model deployment.

Deprecated
```
```

### [Reference](/documentation/CoreML#Reference)

[

API Reference

CoreML Enumerations](/documentation/coreml/coreml-enumerations)

### [Functions](/documentation/CoreML#Functions)

```swift
```swift
```swift
```swift
func pointwiseMax(some MLTensorScalar & Numeric, MLTensor) -> MLTensor
```
```

Computes the element-wise maximum of two values.

Beta
```
```swift
```swift
```swift
func pointwiseMax(MLTensor, MLTensor) -> MLTensor
```
```

Computes the element-wise minimum between two tensors.
```
```swift
```swift
```swift
func pointwiseMax(MLTensor, some MLTensorScalar & Numeric) -> MLTensor
```
```

Computes the element-wise maximum of two values.

Beta
```
```swift
```swift
```swift
func pointwiseMin(MLTensor, MLTensor) -> MLTensor
```
```

Computes the element-wise minimum of two tensors.
```
```swift
```swift
```swift
func pointwiseMin(MLTensor, some MLTensorScalar & Numeric) -> MLTensor
```
```

Computes the element-wise minimum of two values.

Beta
```
```swift
```swift
```swift
func pointwiseMin(some MLTensorScalar & Numeric, MLTensor) -> MLTensor
```
```

Computes the element-wise minimum between two values.

Beta
```
```

### [Enumerations](/documentation/CoreML#Enumerations)

```swift
```swift
```swift
```swift
enum MLShapedArrayBufferLayout
```
```

Buffer layout enum
```
```