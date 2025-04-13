

- Create ML Components
- MLModelImageFeatureExtractor
-  init(contentsOf:configuration:inputName:outputName:context:) 

Initializer

# init(contentsOf:configuration:inputName:outputName:context:)

Creates an image feature extractor from a CoreML model URL.

iOS 16.0+iPadOS 16.0+Mac Catalyst 16.0+macOS 13.0+tvOS 16.0+visionOS 1.0+

``` source
init(
    contentsOf url: URL,
    configuration: MLModelConfiguration,
    inputName: String = "image",
    outputName: String,
    context: CIContext = CIContext()
) async throws
```

## Parameters 

`url`  

URL of the .mlmodel file.

`configuration`  

The model configuration of the CoreML model.

`inputName`  

The name of the input which the `model` expects.

`outputName`  

The name of the output from the `model`.

`context`  

The Core Image context.

## See Also

### Creating the extractor

init(model: MLModel, inputName: String, outputName: String, context: CIContext) throws

Creates an image feature extractor from a CoreML model.

