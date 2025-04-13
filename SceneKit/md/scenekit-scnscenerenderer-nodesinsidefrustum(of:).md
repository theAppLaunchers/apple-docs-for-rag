

- SceneKit
- SCNSceneRenderer
-  nodesInsideFrustum(of:) 

Instance Method

# nodesInsideFrustum(of:)

Returns all nodes that might be visible from a specified point of view.

iOS 9.0+iPadOS 9.0+Mac Catalyst 13.1+macOS 10.11+tvOS 9.0+visionOS 1.0+watchOS 2.0+

``` source
func nodesInsideFrustum(of pointOfView: SCNNode) -> [SCNNode]
```

**Required**

## Parameters 

`pointOfView`  

A node defining a point of view, as used by the pointOfView property.

## Return Value

An array of nodes whose bounding boxes intersect the view frustum defined by the `pointOfView` node. If the array is empty, no nodes lie within the specified frustum.

## Discussion

Any node containing a camera or spotlight may serve as a point of view (see the pointOfView property for details). Such a node defines a *viewing frustum*—a portion of the scene’s coordinate space, shaped like a truncated pyramid, that encloses all points visible from that point of view.

Use this method find all nodes whose content lies within the viewing frustum defined by another node (which may or may not be the scene renderer’s current pointOfView node).

Note that this method does not perform occlusion testing. That is, the returned array includes any node that lies within the specified viewing frustum regardless of whether that node’s contents are obscured by other geometry.

## See Also

### Working With Projected Scene Contents

func hitTest(CGPoint, options: [SCNHitTestOption : Any]?) -> [SCNHitTestResult]

Searches the renderer’s scene for objects corresponding to a point in the rendered image.

**Required**

struct SCNHitTestOption

Options affecting the behavior of SceneKit hit-testing methods.

func isNode(SCNNode, insideFrustumOf: SCNNode) -> Bool

Returns a Boolean value indicating whether a node might be visible from a specified point of view.

**Required**

func projectPoint(SCNVector3) -> SCNVector3

Projects a point from the 3D world coordinate system of the scene to the 2D pixel coordinate system of the renderer.

**Required**

func unprojectPoint(SCNVector3) -> SCNVector3

Unprojects a point from the 2D pixel coordinate system of the renderer to the 3D world coordinate system of the scene.

**Required**

