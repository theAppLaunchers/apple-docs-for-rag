

- Model I/O
-  MDLSubmeshTopology 

Class

# MDLSubmeshTopology

A description of how a submesh’s index buffer data is arranged and how that arrangement should be used to produce the submesh’s intended 3D shape.

iOS 9.0+iPadOS 9.0+Mac Catalyst 13.1+macOS 10.11+tvOS 9.0+visionOS 1.0+

``` source
class MDLSubmeshTopology
```

## Overview

Model I/O creates topology objects when importing assets containing non-uniform index buffers (that is, index buffers not composed of a single primitive type such as triangles or quads). You can also use topology objects (or load assets from file formats supporting topology information) to describe models for surface subdivision, identifying which edges or vertices remain sharp or become smooth when you use the newSubdividedMesh(_:submeshIndex:subdivisionLevels:) method.

## Topics

### Identifying Faces

var faceTopology: (any MDLMeshBuffer)?

A buffer identifying the faces in the submesh and the number of vertices in each.

var faceCount: Int

The number of faces in the submesh’s face topology buffer.

### Identifying Creases

var edgeCreaseIndices: (any MDLMeshBuffer)?

A buffer containing vertex indices that describe edges to be treated as creases during surface subdivision.

var edgeCreases: (any MDLMeshBuffer)?

A buffer containing sharpness values to be applied to edges during surface subdivision.

var edgeCreaseCount: Int

The number of entries in the edge creases buffers.

var vertexCreaseIndices: (any MDLMeshBuffer)?

A buffer containing vertex indices to be treated as creases during surface subdivision.

var vertexCreases: (any MDLMeshBuffer)?

A buffer containing sharpness values to be applied to points during surface subdivision.

var vertexCreaseCount: Int

The number of entries in the vertex creases buffers.

### Identifying Holes

var holes: (any MDLMeshBuffer)?

An index buffer identifying faces to be treated as holes in the mesh during surface subdivision.

var holeCount: Int

The number of entries in the holes buffer.

### Initializers

init(submesh: MDLSubmesh)

## Relationships

### Inherits From

- NSObject

### Conforms To

- CVarArg
- CustomDebugStringConvertible
- CustomStringConvertible
- Equatable
- Hashable
- NSObjectProtocol

## See Also

### 3D Asset Basics

class MDLAsset

An indexed container for 3D objects and associated information, such as transform hierarchies, meshes, cameras, and lights.

class MDLObject

The base class for objects that are part of a 3D asset, including meshes, cameras, and lights.

class MDLTransform

A description of the local coordinate space transformations for a 3D object.

class MDLMesh

A container for vertex buffer data to be used in rendering a 3D object.

class MDLSubmesh

A container for index buffer data and material information to be used in rendering all or part of a 3D object.

protocol MDLNamed

The common interface for Model I/O objects that expose a human-readable name.

