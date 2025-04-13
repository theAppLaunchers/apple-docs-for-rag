

- Model I/O
- MDLSubmeshTopology
-  holes 

Instance Property

# holes

An index buffer identifying faces to be treated as holes in the mesh during surface subdivision.

iOS 9.0+iPadOS 9.0+Mac Catalyst 13.1+macOS 10.11+tvOS 9.0+visionOS 1.0+

``` source
var holes: (any MDLMeshBuffer)? { get set }
```

## Discussion

This buffer contains integer values where each integer is the index of a face to be treated as a hole. For example, if there are two holes in a mesh, then this buffer has two entries.

Because the number of entries in this buffer is likely to be different than the number of entries in any other vertex buffer, it shouldn’t be interleaved with other data in the mesh.

## See Also

### Identifying Holes

var holeCount: Int

The number of entries in the holes buffer.

