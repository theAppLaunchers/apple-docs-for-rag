

- SwiftUI
- Layout
-  updateCache(\_:subviews:) 

Instance Method

# updateCache(\_:subviews:)

Updates the layout’s cache when something changes.

iOS 16.0+iPadOS 16.0+Mac Catalyst 16.0+macOS 13.0+tvOS 16.0+visionOS 1.0+watchOS 9.0+

``` source
func updateCache(
    _ cache: inout Self.Cache,
    subviews: Self.Subviews
)
```

**Required** Default implementation provided.

## Parameters 

`cache`  

Storage for calculated data that you share among the methods of your custom layout container.

`subviews`  

A collection of proxy instances that represent the views arranged by the container. You can use the proxies in the collection to get information about the subviews as you calculate values to store in the cache.

## Discussion

If your custom layout container creates a cache by implementing the makeCache(subviews:) method, SwiftUI calls the update method when your layout or its subviews change, giving you an opportunity to modify or invalidate the contents of the cache. The method’s default implementation recreates the cache by calling the makeCache(subviews:) method, but you can provide your own implementation to take an incremental approach, if appropriate.

## Default Implementations

### Layout Implementations

func updateCache(inout Self.Cache, subviews: Self.Subviews)

Reinitializes a cache to a new value.

## See Also

### Managing a cache

func makeCache(subviews: Self.Subviews) -> Self.Cache

Creates and initializes a cache for a layout instance.

**Required** Default implementation provided.

associatedtype Cache = Void

Cached values associated with the layout instance.

**Required**

