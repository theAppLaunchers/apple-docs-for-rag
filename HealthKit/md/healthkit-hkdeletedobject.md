

- HealthKit
-  HKDeletedObject 

Class

# HKDeletedObject

An object that represents a sample that has been deleted from the HealthKit store.

iOS 9.0+iPadOS 9.0+Mac Catalyst 13.0+macOS 13.0+visionOS 1.0+watchOS 2.0+

``` source
class HKDeletedObject
```

## Mentioned in 

About the HealthKit framework

## Overview

Use HKAnchoredObjectQuery queries to generate a list of recently deleted objects. Create a query using the init(type:predicate:anchor:limit:resultsHandler:)method. When the system calls the result handler, it passes the `deletedObject` parameter an array of HKDeletedObject instances matching the query.

Deleted objects are temporary; the system may remove them from the HealthKit store at any time to free up space. To guarantee that you receive notifications for all deleted objects, create an HKObserverQuery and register it for background delivery. The system then wakes your app and calls the observer query’s update handler whenever the matching objects change—including deletions. However, the query does not provide a list of deleted objects. To determine which objects were deleted, use the observer query’s update handler to create an anchored object query for the newly deleted objects.

## Topics

### Identifying Deleted Objects

var uuid: UUID

The universally unique identifier (UUID) for the HealthKit object that was deleted from the store.

var metadata: [String : Any]?

The metadata associated with the deleted object.

## Relationships

### Inherits From

- NSObject

### Conforms To

- CVarArg
- CustomDebugStringConvertible
- CustomStringConvertible
- Equatable
- Hashable
- NSCoding
- NSObjectProtocol
- NSSecureCoding
- Sendable

