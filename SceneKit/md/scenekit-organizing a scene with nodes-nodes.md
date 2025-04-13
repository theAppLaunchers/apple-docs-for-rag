

- SceneKit
-  Organizing a Scene with Nodes 

Article

# Organizing a Scene with Nodes

Use nodes to define the structure of a scene.

## Overview

SceneKit implements content as a hierarchical tree structure of nodes, also known as a *scene graph*. A scene consists of a root node, which defines a coordinate space for the world of the scene, and other nodes that populate the world with visible content. SceneKit displays scenes in a view, processing the scene graph and performing animations before efficiently rendering each frame on the GPU.

Before working with SceneKit, you should be familiar with basic graphics concepts such as coordinate systems and the mathematics of three-dimensional geometry. SceneKit uses a right-handed coordinate system where (by default) the direction of view is along the negative z-axis, as illustrated below.

## See Also

### Scene Structure

class SCNNode

A structural element of a scene graph, representing a position and transform in a 3D coordinate space, to which you can attach geometry, lights, cameras, or other displayable content.

class SCNReferenceNode

A scene graph node that serves as a placeholder for content to be loaded from a separate scene file.

