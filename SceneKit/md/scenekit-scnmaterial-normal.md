

- SceneKit
- SCNMaterial
-  normal 

Instance Property

# normal

An object that defines the nominal orientation of the surface at each point for use in lighting.

iOSiPadOSMac CatalystmacOStvOSvisionOSwatchOS

``` source
var normal: SCNMaterialProperty { get }
```

## Discussion

Simulating the interaction of lights with a material requires information about the orientation of the surface at each point. Typically, normal vectors provided by a geometry object provide this information. However, this limits the level of detail for surface contours because a geometry can only provide one unique surface normal vector per vertex (and increasing vertex count to model a highly detailed surface exacts a high performance cost).

Alternatively, you can use a texture image as a *normal map* that describes the orientation of a surface for each pixel in the texture. When SceneKit uses an image, it treats the R, G, and B components of each as the X, Y, and Z components of a surface normal vector. Because a normal map texture can store much more detailed surface information than a geometry, you can use a material’s normal property to simulate rough surfaces such as stone or add embossed or engraved designs to an otherwise smooth surface.

By default, the normal property’s contents object is a white color. Setting the normal property’s contents to any solid color disables normal mapping, causing SceneKit to shade the material using only the surface normal information provided by its geometry. Setting the normal property’s contents to an image or other texture-mapped content enables normal mapping, which also automatically sets the material’s isLitPerPixel property to true.

The figure below shows the effect of setting the normal property’s contents to a texture image on a material whose other properties have default contents.

The material’s lightingModel property determines the formula SceneKit uses to combine its surface normals and other visual properties with lights and other contents in a scene to produce the final color for each rendered pixel in the rendered scene. For details, see `Lighting Models`.

## See Also

### Related Documentation

var specular: SCNMaterialProperty

An object that manages the material’s specular response to lighting.

var reflective: SCNMaterialProperty

An object that defines the reflected color for each point on a surface.

var multiply: SCNMaterialProperty

An object that provides color values that are multiplied with pixels in a material after all other shading is complete.

var ambient: SCNMaterialProperty

An object that manages the material’s response to ambient lighting.

var transparent: SCNMaterialProperty

An object that determines the opacity of each point in a material.

### Visual Properties for Special Effects

var displacement: SCNMaterialProperty

var emission: SCNMaterialProperty

An object that defines the color emitted by each point on a surface.

var selfIllumination: SCNMaterialProperty

An object that provides color values representing the global illumination of the surface.

var ambientOcclusion: SCNMaterialProperty

An object that provides color values to be multiplied with the ambient light affecting the material.

