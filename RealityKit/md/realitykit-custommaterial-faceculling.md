

- RealityKit
- CustomMaterial
-  faceCulling 

Instance Property

# faceCulling

A process in which the system specifies polygons to remove before rendering a mesh using this material.

iOS 15.0+iPadOS 15.0+Mac Catalyst 15.0+macOS 12.0+

``` source
var faceCulling: CustomMaterial.FaceCulling { get set }
```

## Discussion

To improve performance, RealityKit culls polygons, or *faces*, that it determines won’t be visible. Discarding faces that aren’t part of the final render eliminates the need to do any calculations for those faces.

RealityKit recognizes when a face aims toward the camera (a *front face*) or away from the camera (a *back face*). This value controls the type of faces RealityKit culls.

The default for this value is MaterialParameterTypes.FaceCulling.back, which means RealityKit removes faces that point away from the camera. Because back faces point away from the camera and are usually obscured by front-facing polygons, the user typically won’t see them. As a result, in most cases, the default setting is desirable because it culls polygons that don’t contribute to the rendered scene.

You can change the culling behavior to cull front faces instead or to turn off face culling altogether, but be aware that turning off face culling results in less efficient rendering and may negatively impact your app’s frame rate.

