

- Metal
- MTLRenderPipelineDescriptor
-  binaryArchives 

Instance Property

# binaryArchives

An array of binary archives to search for precompiled versions of the shader.

iOS 14.0+iPadOS 14.0+Mac Catalyst 14.0+macOS 11.0+tvOS 14.0+visionOS 1.0+

``` source
var binaryArchives: [any MTLBinaryArchive]? { get set }
```

## Mentioned in 

Creating Binary Archives from Device-Built Pipeline State Objects

## See Also

### Specifying Precompiled Shader Binaries

var supportAddingVertexBinaryFunctions: Bool

A Boolean value that indicates whether you can use the pipeline to create new pipelines by adding binary functions to the vertex shader’s callable functions list.

var supportAddingFragmentBinaryFunctions: Bool

A Boolean value that indicates whether you can use the pipeline to create new pipelines by adding binary functions to the fragment shader’s callable functions list.

