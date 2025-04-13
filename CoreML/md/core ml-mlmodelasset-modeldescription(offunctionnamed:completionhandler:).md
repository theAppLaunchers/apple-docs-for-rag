

- Core ML
- MLModelAsset
-  modelDescription(ofFunctionNamed:completionHandler:) 

Instance Method

# modelDescription(ofFunctionNamed:completionHandler:)

The model descripton for a specified function.

iOS 18.0+iPadOS 18.0+Mac Catalyst 18.0+macOS 15.0+tvOS 18.0+visionOS 2.0+watchOS 11.0+

``` source
func modelDescription(
    ofFunctionNamed functionName: String,
    completionHandler handler: @escaping (MLModelDescription?, (any Error)?) -> Void
)
```

``` source
func modelDescription(of functionName: String) async throws -> MLModelDescription
```

## Discussion

Use this method to get the description of the model such as the feature descriptions, the model author, and other metadata.

```
let modelAsset = try MLModelAsset(url: modelURL)
let modelDescription = try await modelAsset.modelDescription(of: "my_function")
print(modelDescription)
```

