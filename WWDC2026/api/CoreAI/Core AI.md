- CoreAI  
- Core AI  
  
Framework  
  
# Core AI  
  
Run AI models in your app on Apple silicon.  
  
iOS 27.0+ iPadOS 27.0+ Mac Catalyst 27.0+ macOS 27.0+ tvOS 27.0+ visionOS 27.0+ watchOS 27.0+  
  
## Overview  
  
Core AI helps you build, run, and deploy AI models in your app. Designed with Apple silicon in mind, Core AI allows your app to use the latest model architectures and inference techniques across the CPU, GPU, and Neural Engine. The Swift API makes common tasks simple, while giving you more control over model specialization, caching, and inference performance when needed.  
  
Alongside the framework, Core AI includes additional tools for model preparation, integration, and debugging. Prepare your models for Apple silicon with Core AI Optimization, then convert them into the .aimodel format with Core AI PyTorch Extensions. The Core AI Debugger app supports visualization and numeric debugging, letting you inspect model structure and trace tensor values directly back to your Python source code.  
  
Core AI also integrates with Xcode and the developer toolchain. The Core AI debug gauge and Core AI instrument help you monitor and profile inference performance in your app. You can also compile models ahead of time with the coreai-build command-line tool.  
  
If your app uses model types other than neural networks, such as decision trees or tabular feature engineering, see Core ML.  
  
## Topics  
  
### Essentials  
  
Integrating on-device AI models in your app with Core AI  
Power your app’s intelligent features with an on-device AI model.  
  
struct AIModel  
  
A specialized model for running inference on a device.  
  
struct AIModelAsset  
  
An unspecialized source model asset.  
  
### Inference  
  
struct InferenceFunction  
  
A function that performs inference on input values and produces output values.  
  
struct InferenceFunctionDescriptor  
  
A description of an inference function’s signature.  
  
struct InferenceValue  
  
A value that an inference function accepts as input or produces as output.  
  
struct ImageDescriptor  
  
A description of an image’s dimensions and pixel format.  
  
class ComputeStream  
  
A stream of work to be run asynchronously.  
  
### Multidimensional arrays  
  
struct NDArray  
  
A multidimensional array of scalar values used for model inference.  
  
struct NDArrayDescriptor  
  
A description of an array’s shape, scalar type, and memory layout expectations.  
  
### Configuration  
  
Managing model specialization and caching  
  
Configure model specialization, manage cached assets, and reduce your app’s storage footprint.  
  
Compiling Core AI models ahead of time  
  
Reduce on-device specialization time by compiling Core AI models at build time.  
  
class AIModelCache  
  
A cache that stores the specialized model artifacts for inference.  
  
enum ComputeUnitKind  
  
A type of hardware compute unit available for model inference.  
  
struct SpecializationOptions  
  
### Debugging and performance  
  
Inspecting, debugging, and profiling Core AI models  
  
Investigate model behavior, monitor activity, and profile performance using the Core AI tools across Xcode and the Core AI Debugger app.  
  
### Errors  
  
struct AssetError  
  
An error that occurs during model asset operations.  
