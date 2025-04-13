

- RealityKit
- Entity
-  Loading entities from a file 

Article

# Loading entities from a file

Retrieve an entity from storage on disk using a synchronous or an asynchronous load operation.

## Overview

Use a load method to bring an entity stored in a file into your app. You can load USD files (.usd, .usda, .usdc, .usdz) and Reality files (.reality) this way. You get a Reality file by exporting a project from the Reality Composer app, as described in Creating 3D Content with Reality Composer.

### Load an entity hierarchy synchronously

Use the `load(named:in:)` method to load an entity hierarchy from a USD or Reality file stored in a bundle. This method returns only after the operation completes. Omit the bundle parameter from the method call to load from the app’s main bundle:

```
let entity = try? Entity.load(named: "MyEntity") 
```

To load an entity stored at a specific location in the file system, create a file URL and use the load(contentsOf:withName:) method instead:

```
let url = URL(fileURLWithPath: "path/to/MyEntity.usdz")
let entity = try? Entity.load(contentsOf: url)
```

The load methods preserve the entity hierarchy in the loaded file and return the root entity in the scene that the USD or Reality file contains. The entity can have any number of descendant entities that you access using the methods of the HasHierarchy protocol. Accessing entities this way enables you to store and import sophisticated compositions from a single asset.

### Load an entity hierarchy asynchronously

Synchronous load operations block the thread on which you call them. To maintain a smooth user interface, use an asynchronous load instead. The entity initializer has an asynchronous overload. For example, load from a bundle asynchronously by calling the method:

```
_ = try! await Entity(named: "MyEntity")   // From the app's main bundle.
```

Call the asynchronous version of these initializers by prefacing the call with the await keyword from asynchronous methods or from inside of a Task These overloads give you access to the full set of features Concurrency provides.

### Load an anchor entity

When you want to load a composition rooted by an anchor entity, you can instead use the loadAnchor(named:in:) method, or one of its siblings. These methods behave like the related load methods, except that they specifically return an AnchorEntity instance that you can add to your scene:

```
if let anchor = try? Entity.loadAnchor(named: "MyEntity") {
    arView.scene.addAnchor(anchor)
}
```

As with the load methods, the load anchor methods preserve the entity hierarchy.

Note

The load anchor methods work only for Reality files.

### Load a flattened model or body-tracked entity

To load a model or body-tracked entity with internal structure that you don’t need to access, use the loadModel(named:in:) or the loadBodyTracked(named:in:) method, respectively. These methods and their siblings flatten the entity hierarchy into a single entity cast either as a ModelEntity or BodyTrackedEntity. A flattened entity can be easier to work with when you don’t need access to the entity’s details.

Note

The load model and body-tracked methods work only for USD files.

## See Also

### Loading an entity from a file

Stored entities

Manage entities that you store as assets on disk.

Creating USD files for Apple devices

Generate 3D assets that render as expected.

convenience init(contentsOf: URL, withName: String?) async throws

Creates an entity by asynchronously loading it from a file URL.

convenience init(named: String, in: Bundle?) async throws

Creates an entity by asynchronously loading it from a bundle.

struct ReferenceComponent

A component that can load another entity from a file.

