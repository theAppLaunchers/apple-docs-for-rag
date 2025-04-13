

- Core Data
- NSEntityDescription
-  uniquenessConstraints 

Instance Property

# uniquenessConstraints

An array of arrays that contains one or more attributes with a value that must be unique over the instances of that entity.

iOS 9.0+iPadOS 9.0+Mac Catalyst 13.1+macOS 10.11+tvOS 9.0+visionOS 1.0+watchOS 2.0+

``` source
var uniquenessConstraints: [[Any]] { get set }
```

## Discussion

Each inner array contains one or more NSAttributeDescription objects or strings that contain the names of attributes on the entity.

This value forms part of the entity’s version hash. Stores that don’t support uniqueness constraints must refuse to initialize when receiving a model that contains such constraints.

Note

Uniqueness constraint violations can be computationally expensive to handle. The recommendation is to use only one uniqueness constraint per entity hierarchy, although subentites may extend a superentity’s constraint.

## See Also

### Configuring indexes and constraints

var indexes: [NSFetchIndexDescription]

An array of fetch index descriptions for the entity.

var compoundIndexes: [[Any]]

The compound indexes for the entity as an array of arrays.

Deprecated

