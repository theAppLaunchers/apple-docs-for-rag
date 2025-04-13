

- Create ML Components
- ComposedTemporalTransformer
-  export(to:metadata:) 

Instance Method

# export(to:metadata:)

Exports this temporal transformer as a CoreML model with user-supplied metadata.

iOS 17.0+iPadOS 17.0+Mac Catalyst 17.0+macOS 14.0+tvOS 17.0+visionOS 1.0+

``` source
func export(
    to url: URL,
    metadata: ModelMetadata
) throws
```

## Parameters 

`url`  

The location to write the model into.

`metadata`  

Contextual user-provided information.

## Discussion

Note

By default this method exports .mlpackage files. You can export a .mlmodel file by specifying that as the URL file extension. But if you specify .mlmodel and the transformer doesn’t support it, this method will throw an error.

