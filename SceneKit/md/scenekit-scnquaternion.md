

- SceneKit
-  SCNQuaternion 

Type Alias

# SCNQuaternion

A representation of a quaternion.

iOSiPadOSMac CatalystmacOStvOSvisionOSwatchOS

``` source
typealias SCNQuaternion = SCNVector4
```

## Discussion

A quaternion is a mathematical construct useful for describing rotations in three-dimensional space. Although its implementation differs from that of a 4-component vector, you specify a quaternion value using the same fields as an `SCNVector4` structure.

SceneKit uses unit quaternions (those whose components satisfy the equation `x*x + y*y + z*z + w*w == 1`) for the orientation property of nodes.

## See Also

### Transforms and Rotations

struct SCNMatrix4

A representation of a 4 x 4 matrix.

typealias SCNMatrix4

A representation of a 4 x 4 matrix.

