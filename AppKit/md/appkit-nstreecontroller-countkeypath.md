

- AppKit
- NSTreeController
-  countKeyPath 

Instance Property

# countKeyPath

The key path used to find the number of children for a node.

macOS

``` source
var countKeyPath: String? { get set }
```

## Discussion

Specifying this key path (if the data is available in the model object) can increase performance, but disables insert and remove functionality.

## See Also

### Specifying model attributes

var childrenKeyPath: String?

The key path used to find the children in the tree controller’s objects.

func childrenKeyPath(for: NSTreeNode) -> String?

Returns the key path used to find the children in the specified tree node.

func countKeyPath(for: NSTreeNode) -> String?

Returns the key path that provides the number of children for a specified node.

var leafKeyPath: String?

The key path used by the tree controller to determine if a node is a leaf key.

func leafKeyPath(for: NSTreeNode) -> String?

Returns the key path that specifies whether the node is a leaf node.

