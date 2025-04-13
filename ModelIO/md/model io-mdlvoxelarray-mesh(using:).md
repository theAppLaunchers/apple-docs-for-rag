

- Model I/O
- MDLVoxelArray
-  mesh(using:) 

Instance Method

# mesh(using:)

Generates a closed polygon mesh around the volume of space the voxel array describes.

iOS 9.0+iPadOS 9.0+Mac Catalyst 13.1+macOS 10.11+tvOS 9.0+visionOS 1.0+

``` source
func mesh(using allocator: (any MDLMeshBufferAllocator)?) -> MDLMesh?
```

## Parameters 

`allocator`  

An object responsible for allocating mesh vertex data. If `nil`, Model I/O uses an internal allocator object.

## Return Value

A new mesh object.

## Discussion

Use this method to create a polygon mesh for use in rendering the object described by the voxel array.

The `allocator` parameter controls vertex data allocation for the mesh. For example, to use the MetalKit framework for loading vertex data into GPU buffers for rendering using Metal, pass a MTKMeshBufferAllocator object. By specifying an allocator, you can ensure that mesh data is copied a minimal number of times between being generated and being loaded into GPU memory for rendering.

