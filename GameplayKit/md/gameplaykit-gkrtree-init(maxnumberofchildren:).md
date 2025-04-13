

- GameplayKit
- GKRTree
-  init(maxNumberOfChildren:) 

Initializer

# init(maxNumberOfChildren:)

Initializes a new R-tree object.

iOS 10.0+iPadOS 10.0+Mac Catalyst 13.1+macOS 10.12+tvOS 10.0+visionOS 1.0+

``` source
init(maxNumberOfChildren: Int)
```

## Parameters 

`maxNumberOfChildren`  

The maximum number of children for each tree node.

## Return Value

A new R-tree object.

## Discussion

An R-tree, like other tree data structures, is a collection of nodes, each of which contains one of the objects stored in the tree. You don’t directly interact with nodes—GameplayKit automatically creates and manages them, so you interact only with the objects the nodes contain. However, the `maxNumberOfChildren` parameter determines when the R-tree automatically reorganizes its internal structure, and thus the performance of the add and search operations.

A larger `maxNumberOfChildren` value means that the tree reorganizes itself less often. Therefore, the performance of the addElement(_:boundingRectMin:boundingRectMax:splitStrategy:) method is faster (on average, across many calls). But because each node contains a larger number of elements, the performance of the elements(inBoundingRectMin:rectMax:) method is slower (on average). A smaller `maxNumberOfChildren` value reverses the situation, improving performance for search operations at the cost of performance for add operations.

For more information, see GameplayKit Programming Guide.

