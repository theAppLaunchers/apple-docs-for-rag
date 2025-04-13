

- HealthKit
- Queries
- HKSourceQuery
-  Executing Source Queries 

Article

# Executing Source Queries

Create and run source queries.

## Overview

Source queries return a list of apps and devices that have saved data to the HealthKit store. The query returns all sources for the specified sample type.

### Create Source Queries

You create a source query by calling the init(sampleType:samplePredicate:completionHandler:) initializer. Start by creating the type object for the desired samples. The following example creates a type object for step counts.

```
guard let stepCountType = HKObjectType.quantityType(forIdentifier: .stepCount) else {
    // This should never fail when using a defined constant.
    fatalError("*** Unable to get the step count type ***")
}
```

Then use the type object to create the query. Source queries return a list of sources (apps and devices) that have saved queries matching the sample type. The callback handler should check for errors before processing the sources. It should also dispatch updates to the user interface back to the main thread.

```
let query = HKSourceQuery(sampleType: stepCountType, samplePredicate: nil) { (query, sourcesOrNil, errorOrNil) in

    guard let sources = sourcesOrNil else {
        // Properly handle the error.
        return
    }

    for source in sources {
        // Process sources here.
    }

    DispatchQueue.main.async {
        // Update the UI here.
    }
}
```

### Run the Query

After the query is instantiated, you run it by calling the HealthKit store’s execute(_:) method.

```
store.execute(query)
```

This runs the query on an anonymous background queue. When the query is complete, it executes the results handler on the same background queue (but not necessarily the same thread).

## See Also

### Creating Source Queries

init(sampleType: HKSampleType, samplePredicate: NSPredicate?, completionHandler: (HKSourceQuery, Set&lt;HKSource>?, (any Error)?) -> Void)

Instantiates and returns a source query.

