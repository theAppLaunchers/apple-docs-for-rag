

- PHASE
- PHASEObject
-  removeChild(\_:) 

Instance Method

# removeChild(\_:)

Removes the given object as a child.

iOS 15.0+iPadOS 15.0+Mac Catalyst 15.0+macOS 12.0+tvOS 17.0+visionOS 1.0+

``` source
func removeChild(_ child: PHASEObject)
```

## Parameters 

`child`  

The object to remove from the children array.

## See Also

### Managing the Hierarchy

var children: [PHASEObject]

Objects that position and orient in the scene relative to the given object.

var parent: PHASEObject?

The object that this instance positions and orients relative to in the scene.

func addChild(PHASEObject) throws

Adds the given object as a child.

func removeChildren()

Removes all child objects from the given object.

