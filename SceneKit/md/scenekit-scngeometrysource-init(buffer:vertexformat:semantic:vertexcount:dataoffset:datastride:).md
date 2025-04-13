

- SceneKit
- SCNGeometrySource
-  init(buffer:vertexFormat:semantic:vertexCount:dataOffset:dataStride:) 

Initializer

# init(buffer:vertexFormat:semantic:vertexCount:dataOffset:dataStride:)

Creates a geometry source whose vertex data resides in the specified Metal buffer, allowing modification through a Metal compute shader.

iOS 9.0+iPadOS 9.0+Mac Catalyst 13.1+macOS 10.11+tvOS 9.0+visionOS 1.0+

``` source
convenience init(
    buffer: any MTLBuffer,
    vertexFormat: MTLVertexFormat,
    semantic: SCNGeometrySource.Semantic,
    vertexCount: Int,
    dataOffset offset: Int,
    dataStride stride: Int
)
```

## Parameters 

`buffer`  

A Metal buffer containing per-vertex data for the geometry source.

`vertexFormat`  

The type of per-vertex data in the buffer. A MTLVertexFormat value defines the number of components for each vector in the geometry source and the data type and size of each component.

`semantic`  

The semantic value (or attribute) that the geometry source describes for each vertex. See Geometry Semantic Identifiers for available values.

`vertexCount`  

The number of vertices in the geometry source.

`offset`  

The offset, in bytes, from the beginning of the data to the first vector component to be used in the geometry source.

`stride`  

The number of bytes from each vector to the next in the data.

## Return Value

A new geometry source object.

## Discussion

Use this method to create a geometry source whose underlying data can be modified at render time by a Metal compute shader running on the GPU. To create a MTLBuffer object for use with a geometry source, use the device property of the SceneKit view (or other renderer) responsible for drawing your scene.

```
// Create and fill a buffer.
id  device = self.scnView.device;
self.geometryBuffer = [device newBufferWithBytes:myData length:myLength options:myOptions];
// Create a geometry source from the buffer.
SCNGeometrySource *source = [SCNGeometrySource geometrySourceWithBuffer:buffer
                             vertexFormat:myVertexFormat
                                 semantic:SCNGeometrySourceSemanticVertex
                              vertexCount:myVertexCount
                               dataOffset:0
                               dataStride:0];
```

Then, to modify the buffer’s contents at render time, implement a scene renderer delegate and schedule a compute command encoder during a render delegate method such as renderer(_:willRenderScene:atTime:).

```
- (void)renderer:(id )aRenderer willRenderScene:(SCNScene *)scene atTime:(NSTimeInterval)time {
     // Get a command buffer and compute encoder from the view (or other renderer).
     id myCommandBuffer = [aRenderer.commandQueue commandBuffer];
     id myComputeEncoder = [myCommandBuffer computeCommandEncoder];

     // Configure the compute command encoder.
     // (Note pipeline state is preconfigured outside of the render loop.)
     [myComputeEncoder setComputePipelineState:self.pipelineState];
     [myComputeEncoder setBuffer:self.geometryBuffer offset:0 atIndex:0];

     // Schedule the compute command and commit the command buffer.
     [myComputeEncoder dispatchThreadgroups:myThreadgroupCount
                      threadsPerThreadgroup:myThreadCount];
     [myComputeEncoder endEncoding];
     [myCommandBuffer commit];
}
```

Note

Geometry sources backed by a Metal buffer are available only with SceneKit views (or other renderers) whose renderingAPI property is SCNRenderingAPI.metal.

Metal commands that modify the buffer’s contents must be enqueued from within one of the render loop methods defined in the SCNSceneRendererDelegate protocol. The result of attempting to modify a buffer at any other time is undefined.

