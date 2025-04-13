

- AppKit
- NSBezierPath
-  elementCount 

Instance Property

# elementCount

The total number of path elements in the path.

macOS

``` source
var elementCount: Int { get }
```

## Discussion

Each element type corresponds to one of the operations described in Path Elements.

## See Also

### Accessing Elements of a Path

var cgPath: CGPath

func element(at: Int) -> NSBezierPath.ElementType

Returns the type of path element at the specified index.

func element(at: Int, associatedPoints: NSPointArray?) -> NSBezierPath.ElementType

Gets the element type and (and optionally) the associated points for the path element at the specified index.

func removeAllPoints()

Removes all path elements from the path, effectively clearing the path.

func setAssociatedPoints(NSPointArray?, at: Int)

Changes the points associated with the specified path element.

