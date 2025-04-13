

- GameplayKit
- GKPolygonObstacle
-  vertex(at:) 

Instance Method

# vertex(at:)

Returns the point coordinates of the specified vertex.

iOS 9.0+iPadOS 9.0+Mac Catalyst 13.1+macOS 10.11+tvOS 9.0+visionOS 1.0+

``` source
func vertex(at index: Int) -> vector_float2
```

## Parameters 

`index`  

An index to the obstacle’s list of vertices, between zero and the value of the vertexCount property.

## Return Value

The point coordinates of the specified vertex.

## Discussion

Obstacles are immutable objects; to change the shape of an obstacle, remove it and create a new obstacle with a new list of vertices. Use this method along with the vertexCount property to inspect an existing obstacle—for example, to draw a debugging overlay representing the obstacle in your game.

The coordinate space you define obstacles in, whether used for pathfinding or with agents, is entirely arbitrary. However, it is often convenient to define pathfinding graphs and agent simulations in a coordinate space similar to the one your game uses for display—for example, in a SpriteKit game, define obstacles in the point coordinate system of your scene.

## See Also

### Inspecting Vertices

var vertexCount: Int

The number of vertices that define the polygon-shaped area of the obstacle.

