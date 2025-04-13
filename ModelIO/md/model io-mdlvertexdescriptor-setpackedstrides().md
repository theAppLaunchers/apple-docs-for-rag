

- Model I/O
- MDLVertexDescriptor
-  setPackedStrides() 

Instance Method

# setPackedStrides()

Sets the stride for each vertex layout to the minimum value to pack vertex data together in a single buffer.

iOS 9.0+iPadOS 9.0+Mac Catalyst 13.1+macOS 10.11+tvOS 9.0+visionOS 1.0+

``` source
func setPackedStrides()
```

## Discussion

This method examines the offset property of each of the descriptor’s vertex attributes, calculates a stride for each of the descriptor’s vertex layouts that fits vertex data into a single buffer with minimal unused padding space between vertices, then sets the stride property of each vertex layour to the calculated value.

For example, consider a vertex buffer with three attributes: position, normal, and texture coordinate. The position and normal attributes each contain 3-component floating-point vectors for each vertex, and the texture coordinate attribute contains a 2-component floating-point vector for each vertex. The data size for the each of the first two attributes is 12 bytes (4 bytes per component), and the data size for the third is 8 bytes (4 bytes per component). Therefore, if the offset of each attributes is set such that there is no padding between the data for each, the minimum stride that leaves no padding between vertices is 32 bytes (the sum of the sizes of all three attributes).

To describe a fully packed vertex buffer, call this method *after* calling the setPackedOffsets() method.

## See Also

### Working with Vertex Buffer Layouts

var layouts: NSMutableArray

The list of vertex buffer layouts described by the vertex descriptor.

