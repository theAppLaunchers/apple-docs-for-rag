

- SwiftData
- ModelContainer
-  init(for:migrationPlan:configurations:) 

Initializer

# init(for:migrationPlan:configurations:)

Creates a model container using the specified schema, migration plan, and configurations.

iOS 17.0+iPadOS 17.0+Mac Catalyst 17.0+macOS 14.0+tvOS 17.0+visionOS 1.0+watchOS 10.0+Swift 5.9+

``` source
init(
    for givenSchema: Schema,
    migrationPlan: (any SchemaMigrationPlan.Type)? = nil,
    configurations: [ModelConfiguration]
) throws
```

## Parameters 

`givenSchema`  

A schema that maps your app’s model classes to the associated data in the app’s persistent storage. For more information, see Schema.

`migrationPlan`  

A plan that describes the evolution of your app’s schema and how the container migrates between specific versions. For more information, see SchemaMigrationPlan.

`configurations`  

An array of configurations that describe how the container manages the persisted data for specific groups of models. For more information, see ModelConfiguration.

## Discussion

Important

A container must have at least one configuration. If you specify an empty array, the framework creates an instance of ModelConfiguration for you by combining your app’s entitlements with the type’s default values.

## See Also

### Creating a model container

convenience init(for: any PersistentModel.Type..., migrationPlan: (any SchemaMigrationPlan.Type)?, configurations: ModelConfiguration...) throws

Creates a model container using the specified model types, migration plan, and zero or more configurations.

convenience init(for: Schema, migrationPlan: (any SchemaMigrationPlan.Type)?, configurations: ModelConfiguration...) throws

Creates a model container using the specified schema, migration plan, and zero or more configurations.

protocol PersistentModel

An interface that enables SwiftData to manage a Swift class as a stored model.

struct ModelConfiguration

A type that describes the configuration of an app’s schema or specific group of models.

class Schema

An object that maps model classes to data in the model store, and helps with the migration of that data between releases.

protocol SchemaMigrationPlan

An interface for describing the evolution of a schema and how to migrate between specific versions.

