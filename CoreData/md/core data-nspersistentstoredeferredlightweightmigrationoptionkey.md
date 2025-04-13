

- Core Data
-  NSPersistentStoreDeferredLightweightMigrationOptionKey 

Global Variable

# NSPersistentStoreDeferredLightweightMigrationOptionKey

The key for enabling deferred lightweight migrations.

iOS 14.0+iPadOS 14.0+Mac Catalyst 14.0+macOS 11.0+tvOS 14.0+visionOS 1.0+watchOS 7.0+

``` source
let NSPersistentStoreDeferredLightweightMigrationOptionKey: String
```

## Discussion

As your managed object model changes, Core Data can use lightweight migrations to synchronize the underlying store data with those evolving entity definitions. These migrations happen at runtime, so they need to be fast or they can lead to a poor experience, because a migration must complete before your app can continue. Reduce the impact of migrations by deferring expensive cleanup tasks — such as dropping a table — until a more opportune time.

Important

This key is dual-purpose. When adding a persistent store to the coordinator, you use it to enable deferred lightweight migrations for that store. Afterward, Core Data uses it to indicate whether there are deferred cleanup tasks to run. Therefore, don’t use this key to later determine whether you enabled deferred lightweight migrations on a specific store.

Deferred lightweight migrations are off by default. To enable them, add NSPersistentStoreDeferredLightweightMigrationOptionKey, with a value of true, to the options dictionary you provide when adding a persistent store to the coordinator.

```
let options = [
    // Enable deferred lightweight migrations.
    NSPersistentStoreDeferredLightweightMigrationOptionKey: true,
    // Enable lightweight migrations.
    NSMigratePersistentStoresAutomaticallyOption: true,
    NSInferMappingModelAutomaticallyOption: true
]

let store = coordinator.addPersistentStore(
    type: .sqlite,
    at: storeURL,
    options: options
)
```

After you enable deferred lightweight migrations, Core Data continues to perform your lightweight migrations as usual, but defers any time-consuming cleanup tasks that don’t impact the execution of your app. Those tasks still need to run, but you choose when to run them. To determine whether there are deferred tasks to finish, query the store’s metadata with NSPersistentStoreDeferredLightweightMigrationOptionKey. If the returned value is true, execute those tasks using the coordinator. A single migration may defer several distinct tasks and you can execute them all at once using finishDeferredLightweightMigration(), or individually using finishDeferredLightweightMigrationTask().

```
let key = NSPersistentStoreDeferredLightweightMigrationOptionKey
if let hasMigration = store.metadata[key], hasMigration == true {
    coordinator.finishDeferredLightweightMigration()
}
```

## See Also

### Deferring a store’s migrations

func finishDeferredLightweightMigrationTask() throws

Executes a single pending task of a deferred lightweight migration.

func finishDeferredLightweightMigration() throws

Executes all remaining tasks of a deferred lightweight migration.

