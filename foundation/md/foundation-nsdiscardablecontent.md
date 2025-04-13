

- Foundation
-  NSDiscardableContent 

Protocol

# NSDiscardableContent

You implement this protocol when a class’s objects have subcomponents that can be discarded when not being used, thereby giving an application a smaller memory footprint.

iOS 2.0+iPadOS 2.0+Mac Catalyst 13.0+macOS 10.0+tvOS 9.0+visionOS 1.0+watchOS 2.0+

``` source
protocol NSDiscardableContent
```

## Overview

An `NSDiscardableContent` object’s life cycle is dependent upon a “counter” variable. An `NSDiscardableContent` object is a purgeable block of memory that keeps track of whether or not it is currently being used by some other object. When this memory is being read, or is still needed, its counter variable will be greater than or equal to 1. When it is not being used, and can be discarded, the counter variable will be equal to 0.

When the counter is equal to 0, the block of memory may be discarded if memory is tight at that point in time. In order to discard the content, call discardContentIfPossible() on the object, which will free the associated memory if the counter variable equals 0.

By default, `NSDiscardableContent` objects are initialized with their counter equal to 1 to ensure that they are not immediately discarded by the memory-management system. From this point, you must keep track of the counter variable’s state. Calling the beginContentAccess() method increments the counter variable by 1, thus ensuring that the object will not be discarded. When you no longer need the object, decrement its counter by calling endContentAccess().

The Foundation framework includes the NSPurgeableData class, which provides a default implementation of this protocol.

## Topics

### Accessing Content

func beginContentAccess() -> Bool

Returns a Boolean value indicating whether the discardable contents are still available and have been successfully accessed.

**Required**

func endContentAccess()

Called if the discardable contents are no longer being accessed.

**Required**

### Discarding Content

func discardContentIfPossible()

Called to discard the contents of the receiver if the value of the accessed counter is 0.

**Required**

func isContentDiscarded() -> Bool

Returns a Boolean value indicating whether the content has been discarded.

**Required**

## Relationships

### Conforming Types

- NSPurgeableData

## See Also

### Managing Discardable Content

var evictsObjectsWithDiscardedContent: Bool

Whether the cache will automatically evict discardable-content objects whose content has been discarded.

