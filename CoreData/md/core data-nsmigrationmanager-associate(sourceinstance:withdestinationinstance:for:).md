

- Core Data
- NSMigrationManager
-  associate(sourceInstance:withDestinationInstance:for:) 

Instance Method

# associate(sourceInstance:withDestinationInstance:for:)

Associates a given source managed object instance with an array of destination instances for a given property mapping.

iOS 3.0+iPadOS 3.0+Mac Catalyst 13.1+macOS 10.5+tvOSvisionOS 1.0+watchOS 2.0+

``` source
func associate(
    sourceInstance: NSManagedObject,
    withDestinationInstance destinationInstance: NSManagedObject,
    for entityMapping: NSEntityMapping
)
```

## Parameters 

`sourceInstance`  

A source managed object.

`destinationInstance`  

The destination manage object for `sourceInstance`.

`entityMapping`  

The entity mapping to use to associate `sourceInstance` with the object in `destinationInstances`.

## Discussion

Data migration is performed as a three-stage process (first create the data, then relate the data, then validate the data). You use this method to associate data between the source and destination stores, in order to allow for relationship creation or fix-up after the creation stage.

This method is called in the default implementation of `NSEntityMigrationPolicy`’s createDestinationInstances(forSource:in:manager:) method.

## See Also

### Managing Sources and Destinations

func destinationInstances(forEntityMappingName: String, sourceInstances: [NSManagedObject]?) -> [NSManagedObject]

Returns the managed object instances created in the destination store for the named entity mapping for the given array of source instances.

func sourceInstances(forEntityMappingName: String, destinationInstances: [NSManagedObject]?) -> [NSManagedObject]

Returns the managed object instances in the source store used to create the given destination instances for the passed in property mapping.

