

- Core Animation
- CATransaction
-  lock() 

Type Method

# lock()

Attempts to acquire a recursive spin-lock lock, ensuring that returned layer values are valid until unlocked.

iOS 2.0+iPadOS 2.0+Mac Catalyst 13.1+macOS 10.5+tvOS 9.0+visionOS 1.0+

``` source
class func lock()
```

## Discussion

Core Animation uses a data model that promises not to corrupt the internal data structures when called from multiple threads concurrently, but not that data returned is still valid if the property was valid on another thread. By locking during a transaction you can ensure data that is read, modified, and set is correctly managed.

## See Also

### Managing Concurrency

class func unlock()

Relinquishes a previously acquired transaction lock.

