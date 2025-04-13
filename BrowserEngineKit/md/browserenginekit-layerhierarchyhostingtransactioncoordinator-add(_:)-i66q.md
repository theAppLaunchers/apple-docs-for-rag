

- BrowserEngineKit
- LayerHierarchyHostingTransactionCoordinator
-  add(\_:) 

Instance Method

# add(\_:)

a signal to coordinate transactions involving `layerHierarchy` from now until `commit` is called

iOS 17.4+iPadOS 17.4+

``` source
@MainActor
func add(_ layerHierarchy: LayerHierarchy)
```

## Parameters 

`layerHierarchy`  

The object to coordinate transactions for.

## Discussion

Notifies the transaction coordinator to start coordinating transactions for the given layer hierarchy.

## Overview

The transaction coordinator coordinates any transactions involving layers in the `layerHierarchy` until you call commit().

## See Also

### Synchronize transactions

func add(LayerHierarchyHostingView)

Notifies the transaction coordinator to start coordinating transactions for the given view.

func commit()

`commit` must be called on *every* instance and it must be the last call to each instance. note that it does not commit `CATransaction`s but rather commits the coordination of transactions in the render server. note that coordinators should have as constrained a lifespan as possible and will timeout if held open too long.

