

- HealthKit
- HKAnchoredObjectQuery
-  init(queryDescriptors:anchor:limit:resultsHandler:) 

Initializer

# init(queryDescriptors:anchor:limit:resultsHandler:)

Creates an anchored object query that matches any of the query descriptors you provided.

iOS 15.0+iPadOS 15.0+Mac Catalyst 15.0+macOS 13.0+visionOS 1.0+watchOS 8.0+

``` source
init(
    queryDescriptors: [HKQueryDescriptor],
    anchor: HKQueryAnchor?,
    limit: Int,
    resultsHandler handler: @escaping (HKAnchoredObjectQuery, [HKSample]?, [HKDeletedObject]?, HKQueryAnchor?, (any Error)?) -> Void
)
```

## Parameters 

`queryDescriptors`  

An array of descriptors that specify the types of samples that the query returns.

`anchor`  

The anchor that the previous anchored object query returned. The anchor object corresponds to the last object that the previous anchored object query returned. The new query returns only samples and deleted objects that are newer than that object.

Pass `nil` to receive all the matching samples and recently deleted objects currently in the HealthKit store.

`limit`  

The maximum number of samples that the query returned. If you want to return all matching samples, use HKObjectQueryNoLimit.

`handler`  

A block that the HealthKit store calls after gathering the initial results. This block takes the following parameters:

`query`  
A reference to the query calling this block.

`sampleObjects`  
An array containing the samples this query returned, or `nil` if an error occurred.

`deletedObjects`  
An array containing the deleted objects this query returned, or `nil` if an error occurred.

`newAnchor`  
An anchor object corresponding to the last object this query returned. Subsequent anchor queries use this value to receive new samples and deleted objects created after the query returned its initial results.

`error`  
If an error occurs, an object describing the error; otherwise, it’s `nil`.

## Discussion

Use this initializer to create an anchored object query for data that matches any of the HKQueryDescriptor objects. Each descriptor can specify a different data type.

After instantiating the query, call the HKHealthStore class’s execute(_:) method to run it. Queries run on an anonymous background queue. As soon as the query is complete, the system executes the results handler on the background queue, returning samples that match any of the descriptors. You typically dispatch these results to the main queue to update the user interface.

The first time you call this method, pass `nil` as the `anchor` parameter. This method returns all matching objects currently in the HealthKit store. Additionally, save the returned anchor object and pass it to the next query.

Anchor queries can also act as long-running queries. If you assign an update handler before executing the query, the query continues to monitor the HealthKit store after gathering the initial results. The system calls the update handler on a background queue whenever a matching sample is saved to or deleted from the HealthKit store. To cancel this query, call the store’s stop(_:) method.

For example, the following code gathers and returns all step count and push count samples currently in the HeathKit store. It then continues to monitor the store and calls the handler again after any relevant changes.

```
// Create the data types.
let stepCountType = HKQuantityType(.stepCount)
let pushCountType = HKQuantityType(.pushCount)

// Specify the desired sample types.
let stepDescriptor = HKQueryDescriptor(sampleType: stepCountType, predicate: nil)
let pushDescriptor = HKQueryDescriptor(sampleType: pushCountType, predicate: nil)

// Create a handler to process results from the query.
let handler: (HKAnchoredObjectQuery,
              [HKSample]?,
              [HKDeletedObject]?,
              HKQueryAnchor?,
              Error?) -> Void = { (query, samples, deleted, newAnchor, error) in

    if let error = error {
        // Handle errors here.
    }

    DispatchQueue.main.async {
        // Update the anchor.
        anchor = newAnchor

        // Process the samples and deleted objects here.
    }
}

// Create the query.
let anchorQuery = HKAnchoredObjectQuery(queryDescriptors: [stepDescriptor, pushDescriptor],
                                        anchor: anchor,
                                        limit: HKObjectQueryNoLimit,
                                        resultsHandler: handler)

// To continue monitoring the HealthKit store in the background, set the
// update handler.
anchorQuery.updateHandler = handler

// Run the query.
store.execute(anchorQuery)
```

## See Also

### Creating Anchored Object Queries

Executing Anchored Object Queries

Create and run an anchored object query.

init(type: HKSampleType, predicate: NSPredicate?, anchor: HKQueryAnchor?, limit: Int, resultsHandler: (HKAnchoredObjectQuery, [HKSample]?, [HKDeletedObject]?, HKQueryAnchor?, (any Error)?) -> Void)

Initializes a new anchored object query.

let HKObjectQueryNoLimit: Int

A value indicating that the query returns all the matching samples in the HealthKit store.

init(type: HKSampleType, predicate: NSPredicate?, anchor: Int, limit: Int, completionHandler: (HKAnchoredObjectQuery, [HKSample]?, Int, (any Error)?) -> Void)

Initializes a new anchored object query.

Deprecated

