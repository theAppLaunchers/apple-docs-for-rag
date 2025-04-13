

- GameplayKit
- GKObstacleGraph
-  bufferRadius 

Instance Property

# bufferRadius

The distance from obstacle edges that should also be considered impassable.

iOS 9.0+iPadOS 9.0+Mac Catalyst 13.1+macOS 10.11+tvOS 9.0+visionOS 1.0+

``` source
var bufferRadius: Float { get }
```

## Discussion

You set this property when creating a graph with the init(obstacles:bufferRadius:) initializer. Use the `bufferRadius` initializer parameter to take the size of potential travelers into account when determining navigability. After initialization, you can use this property to examine the buffer radius the graph was created with—for example, to draw a debugging overlay in your game UI that indicates passable and impassable areas.

## See Also

### Working with Nodes

func connectUsingObstacles(node: NodeType)

Adds the specified node to the graph, connecting it to its nearest neighbors without creating connections that pass through obstacles or their buffer regions.

func connectUsingObstacles(node: NodeType, ignoring: [GKPolygonObstacle])

Adds the specified node to the graph, connecting it to its nearest neighbors while ignoring the area occupied by the specified obstacles.

func connectUsingObstacles(node: NodeType, ignoringBufferRadiusOf: [GKPolygonObstacle])

Adds the specified node to the graph, connecting it to its nearest neighbors while ignoring the buffer regions around the specified obstacles.

