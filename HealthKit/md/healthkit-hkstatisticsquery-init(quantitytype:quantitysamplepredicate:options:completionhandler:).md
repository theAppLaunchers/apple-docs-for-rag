

- HealthKit
- HKStatisticsQuery
-  init(quantityType:quantitySamplePredicate:options:completionHandler:) 

Initializer

# init(quantityType:quantitySamplePredicate:options:completionHandler:)

Initializes a statistics query instance that performs the specified calculations over the matching samples in the HeathKit store.

iOSiPadOSMac CatalystmacOSvisionOSwatchOS

``` source
init(
    quantityType: HKQuantityType,
    quantitySamplePredicate: NSPredicate?,
    options: HKStatisticsOptions = [],
    completionHandler handler: @escaping (HKStatisticsQuery, HKStatistics?, (any Error)?) -> Void
)
```

## Parameters 

`quantityType`  

The type of sample to search for. This type must be an instance of the HKQuantityType class. You cannot perform statistics queries using other sample types.

`quantitySamplePredicate`  

A predicate that limits the results returned by the query. You can pass `nil` if you want to perform the statistical calculation over all the samples of the specified type.

`options`  

A list of options that define the type of statistical calculations performed and the way in which data from multiple sources are merged. For a list of valid options, see HKStatisticsOptions.

`handler`  

A block that is called after the statistical calculations are complete. This block takes the following arguments:

query  
A reference to the query calling this block.

results  
A HealthKit statistics object that contains the requested statistical data, or `nil` if an error occurs.

error  
If an error occurs, this parameter contains an object describing the error; otherwise, it is `nil`.

## Return Value

A newly initialized statistics query object.

## Mentioned in 

Executing Statistical Queries

## Discussion

After instantiating the query, call the `HKHealthStore` class’s `executeQuery:` method to run this query. Queries run on an anonymous background queue. As soon as the query is complete, the results handler is executed on the same background queue (but not necessarily on the same thread). You typically dispatch these results to the main queue to update the user interface.

Note

Statistical calculations can take a considerable amount of time, especially if there are a large number of samples involved.

## See Also

### Creating Statistics Queries

Executing Statistical Queries

Create and run statistical queries.

