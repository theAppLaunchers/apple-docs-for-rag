

- SwiftData
- ModelConfiguration
-  init(\_:schema:url:allowsSave:cloudKitDatabase:) 

Initializer

# init(\_:schema:url:allowsSave:cloudKitDatabase:)

Creates a named model configuration that specifies the on-disk location of the schema’s persistent storage.

iOS 17.0+iPadOS 17.0+Mac Catalyst 17.0+macOS 14.0+tvOS 17.0+visionOS 1.0+watchOS 10.0+Swift 5.9+

``` source
init(
    _ name: String? = nil,
    schema: Schema? = nil,
    url: URL,
    allowsSave: Bool = true,
    cloudKitDatabase: ModelConfiguration.CloudKitDatabase = .automatic
)
```

## Parameters 

`name`  

An optional name for the model configuration.

`schema`  

A schema that maps model classes to the associated data in the persistent storage. For more information, see Schema.

`url`  

The on-disk location of the schema’s persistent storage.

`allowsSave`  

A Boolean value that determines whether the associated persistent storage is writable. The default value is `true`.

`cloudKitDatabase`  

The option to use for detecting the configuration’s CloudKit database. For possible values, see ModelConfiguration.CloudKitDatabase.

## See Also

### Creating a model configuration

init(isStoredInMemoryOnly: Bool)

Creates a basic model configuration.

init(for: any PersistentModel.Type..., isStoredInMemoryOnly: Bool)

Creates a model configuration for the specified model types.

init(String?, schema: Schema?, isStoredInMemoryOnly: Bool, allowsSave: Bool, groupContainer: ModelConfiguration.GroupContainer, cloudKitDatabase: ModelConfiguration.CloudKitDatabase)

Creates a named model configuration for the specified schema.

