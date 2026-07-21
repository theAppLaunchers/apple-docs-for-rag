# CoreAI/AIModel  
  
- CoreAI  
-  CoreAI.AIModel  
  
Structure  
  
# AIModel  
  
A specialized model for running inference on a device.  
  
iOS 27.0+ iPadOS 27.0+ tvOS 27.0+ visionOS 27.0+ watchOS 27.0+  
  
``` source  
struct AIModel  
```  
  
## Mentioned in  
  
Managing model specialization and caching  
  
Compiling Core AI models ahead of time  
  
Integrating on-device AI models in your app with Core AI  
  
## Overview  
  
An AIModel represents a specialized .aimodel asset, optimized for the current device’s hardware. You create one by loading the asset from disk:  
  
``` source  
let model = try await AIModel(contentsOf: modelURL)  
```  
  
Use functionDescriptor(for:) to inspect a function’s inputs and outputs, then load an InferenceFunction to run inference.  
  
Note  
  
The model instance is lightweight and doesn’t own weights or intermediate buffers. Those resources belong to the functions you load from it.  
  
## Topics  
  
### Creating a model  
  
init(contentsOf: URL, options: SpecializationOptions) async throws  
  
Creates an AIModel from a .aimodelor .aimodelc file.  
  
init?(resolvingBookmark: Data) throws  
  
Create an AIModel by resolving bookmark data pointing to its specialized asset in a cache.  
  
### Loading inference functions  
  
func loadFunction(named: String) throws -> InferenceFunction?  
  
func functionDescriptor(for: String) -> InferenceFunctionDescriptor?  
  
Returns a descriptor for the specified function.  
  
var functionNames: [String]  
  
The names of the inference functions in this model.  
  
### Specializing a model  
  
static func specialize(contentsOf: URL, options: SpecializationOptions, cache: AIModelCache, cachePolicy: AIModelCache.Policy) async throws -> AIModel  
  
Specializes a model for the current device.  
  
### Inspecting a model  
  
var bookmarkData: Data  
  
Create a bookmark for this AIModel’s cached specialized asset entry as serialized data.  
  
static var deviceArchitectureName: String  
  
The Core AI architecture name of the current device.  
  
## Relationships  
  
### Conforms To  
  
- Sendable  
- SendableMetatype  
  
## See Also  
  
### Essentials  
  
Integrating on-device AI models in your app with Core AI  
  
Power your app’s intelligent features with an on-device AI model.  
  
struct AIModelAsset  
  
An unspecialized source model asset.  
