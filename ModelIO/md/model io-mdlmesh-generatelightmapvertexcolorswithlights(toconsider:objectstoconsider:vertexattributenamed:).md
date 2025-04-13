

- Model I/O
- MDLMesh
-  generateLightMapVertexColorsWithLights(toConsider:objectsToConsider:vertexAttributeNamed:) 

Instance Method

# generateLightMapVertexColorsWithLights(toConsider:objectsToConsider:vertexAttributeNamed:)

Calculates static lighting information for the mesh and saves it in the mesh as a vertex color attribute.

iOS 9.0+iPadOS 9.0+Mac Catalyst 13.0+macOS 10.11+tvOS 9.0+visionOS 1.0+

``` source
func generateLightMapVertexColorsWithLights(
    toConsider lightsToConsider: [MDLLight],
    objectsToConsider: [MDLObject],
    vertexAttributeNamed vertexAttributeName: String
) -> Bool
```

## Parameters 

`lightsToConsider`  

An array of lights that should affect the mesh.

`objectsToConsider`  

An array of other objects in the scene that should affect static lighting for the mesh.

`vertexAttributeName`  

The name of the vertex attribute for storing generated vertex color data.

## Return Value

true if light map generation succeeded; otherwise false.

## Discussion

A light map contains, for each point on a surface, information about how light sources in a scene affect the shading of that surface. Because many of the lighting effects in a scene are static—that is, the positions of lights relative to the surfaces they illuminate do not change over time—you can achieve high-fidelity lighting effects with little render-time performance cost by using this method to precalculate (or “bake”) light information into a mesh. You can then use the resulting information in shading to produce a more realistic render.

This method saves light map data as per-vertex colors. Using vertex colors to modulate shading can result in similar results without the texture memory and vertex attribute overhead of a texture map, but the fidelity of this effect depends on the vertex complexity of the mesh. Vertex colors are saved in the vertex attribute specified in the `vertexAttributeName` parameter. If the mesh already contains that attribute, this method overwrites the contents of the corresponding vertex buffer. If the mesh does not contain that attribute, this method creates a new attribute and updates the mesh’s vertexDescriptor object accordingly.

## See Also

### Generating Light Map Data

func generateLightMapTexture(withQuality: Float, lightsToConsider: [MDLLight], objectsToConsider: [MDLObject], vertexAttributeNamed: String, materialPropertyNamed: String) -> Bool

Calculates static lighting information for the mesh and saves it in the mesh as a material property texture.

func generateLightMapTexture(withTextureSize: vector_int2, lightsToConsider: [MDLLight], objectsToConsider: [MDLObject], vertexAttributeNamed: String, materialPropertyNamed: String) -> Bool

Calculates static lighting information for the mesh and saves it in the mesh as a material property texture of the specified size.

