

- SceneKit
- SCNNode
-  hitTestWithSegment(from:to:options:) 

Instance Method

# hitTestWithSegment(from:to:options:)

Searches the node’s child node subtree for objects intersecting a line segment between two specified points.

iOSiPadOSMac Catalyst 13.1+macOS 10.9+tvOSvisionOSwatchOS

``` source
func hitTestWithSegment(
    from pointA: SCNVector3,
    to pointB: SCNVector3,
    options: [String : Any]? = nil
) -> [SCNHitTestResult]
```

## Parameters 

`pointA`  

An endpoint of the line segment to search along, specified in the node’s local coordinate system.

`pointB`  

The other endpoint of the line segment to search along, specified in the node’s local coordinate system.

`options`  

A dictionary of options affecting the search. See Hit Testing Options Keys for acceptable values.

## Return Value

An array of SCNHitTestResult objects representing search results.

## Discussion

Hit-testing is the process of finding elements of a scene located along a specified line segment in the scene’s coordinate space (or that of a particular node in the scene). For example, you can use this method to determine whether a projectile launched by a game character will hit its target.

To search for the scene element corresponding to a two-dimensional point in the rendered image, use the renderer’s hitTest(_:options:) method instead.

## See Also

### Hit-Testing

struct SCNHitTestOption

Options affecting the behavior of SceneKit hit-testing methods.

