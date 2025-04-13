

- SceneKit
- SCNNode
-  rendererDelegate 

Instance Property

# rendererDelegate

An object responsible for rendering custom contents for the node using Metal or OpenGL.

iOSiPadOSMac CatalystmacOStvOSvisionOSwatchOS

``` source
unowned(unsafe) var rendererDelegate: (any SCNNodeRendererDelegate)? { get set }
```

## Discussion

A renderer delegate is a custom object you provide. When SceneKit would otherwise render the contents of the node, it instead tells your delegate to draw contents for the node.

Typically, you use a node renderer delegate for a node that has no associated geometries, cameras, or lights. Such a node only describes a location in space (and a coordinate system transformed by the node hierarchy containing it), which provides an anchor within the scene for whatever custom drawing you want to perform.

If you instead want to customize the results of SceneKit’s geometry and material rendering, use the SCNShadable protocol to attach shaders to SceneKit objects.

## See Also

### Customizing Node Rendering

var filters: [CIFilter]?

An array of Core Image filters to be applied to the rendered contents of the node.

