

- MetalKit
-  Conversion Functions 

API Collection

# Conversion Functions

Convert between Metal and Model I/O vertex representations.

## Topics

### Converting Between Model I/O and Metal Vertex Descriptors

func MTKMetalVertexDescriptorFromModelIO(MDLVertexDescriptor) -> MTLVertexDescriptor?

Returns a partially converted Metal vertex descriptor.

func MTKModelIOVertexDescriptorFromMetal(MTLVertexDescriptor) -> MDLVertexDescriptor

Returns a partially converted Model I/O vertex descriptor.

### Converting Between Model I/O and Metal Vertex Formats

func MTKMetalVertexFormatFromModelIO(MDLVertexFormat) -> MTLVertexFormat

Returns a converted Metal vertex format.

func MTKModelIOVertexFormatFromMetal(MTLVertexFormat) -> MDLVertexFormat

Returns a converted Model I/O vertex format.

## See Also

### Model Handling

class MTKMesh

A container for the vertex data of a Model I/O mesh, suitable for use in a Metal app.

class MTKMeshBuffer

A buffer that backs the vertex data of a Model I/O mesh, suitable for use in a Metal app.

class MTKMeshBufferAllocator

An interface for allocating a MetalKit buffer that backs the vertex data of a Model I/O mesh, suitable for use in a Metal app.

class MTKSubmesh

A container for the index data of a Model I/O submesh, suitable for use in a Metal app.

Model Errors

Learn about errors thrown by model handling methods.

