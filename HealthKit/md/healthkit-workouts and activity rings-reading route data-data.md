

- HealthKit
- Workouts and activity rings
-  Reading route data 

Article

# Reading route data

Access the user’s route for a workout.

## Overview

Your app can read the route associated with any workout in HealthKit (for example, the path that the user took while walking, running, or cycling). However, the size and nature of route data presents two challenges:

- Route samples aren’t static.

- After you have the route sample, you still need to perform a second query to access the underlying location data.

Unlike most HealthKit data, apps can add or update route data over time. For example, an app must save a workout before associating route data with it. This means there is a brief period when the workout exists in the HealthKit store, but it doesn’t yet have a route sample associated with it.

Additionally, apps often post-process the route data. For example, an app may generate and save the initial route sample on Apple Watch, but then perform additional smoothing on iPhone or a remote server. After the smoothing completes, the app updates the route sample using a sync identifier, replacing the original sample with the new, updated version.

As a result, a query that just returns the current route sample for a given workout may return an outdated copy of the route, or may not return anything at all. To guarantee that your app receives the most up-to-date route sample, use an anchored object query to both get the current route, and to track any additions or updates.

After you have the route sample, you still need to make a second query to access the underlying location data. For performance reasons, the system returns the locations asynchronously in batches. As each new batch of location data arrives, your app can process the locations and, for example, plot the locations on a map or analyze and visualize the data.

### Get the Route Sample Object

To guarantee that your app receives the most up-to-date route information, use an anchored object query to access the route and track any updates.

```
let runningObjectQuery = HKQuery.predicateForObjects(from: myWorkout)

let routeQuery = HKAnchoredObjectQuery(type: HKSeriesType.workoutRoute(), predicate: runningObjectQuery, anchor: nil, limit: HKObjectQueryNoLimit) { (query, samples, deletedObjects, anchor, error) in

    guard error == nil else {
        // Handle any errors here.
        fatalError("The initial query failed.")
    }

    // Process the initial route data here.
}

routeQuery.updateHandler = { (query, samples, deleted, anchor, error) in

    guard error == nil else {
        // Handle any errors here.
        fatalError("The update failed.")
    }

    // Process updates or additions here.
}

store.execute(routeQuery)
```

The query’s update handler receives any additions or changes to the route data. This lets your app process the most up-to-date version of the route, as soon as it becomes available.

### Access a Route Sample’s Location Data

After receiving an HKWorkoutRoute sample, you can access its location data using an HKWorkoutRouteQuery. Because a route sample can contain thousands of locations, you may not receive all of the location data at once. Instead, the system returns the location data in small batches.

To process the locations associated with a route:

1.  **Create a query object.** Provide a block to receive the locations.

2.  **Run the query.** Call the HealthKit store’s execute(_:) method to run the query.

3.  **Receive the route data.** Your block receives one or more batches of location data. When the block’s done parameter is true, you have received all the data.

4.  **Optionally:** Call the HealthKit store’s stop(_:) method to stop the query from receiving additional data.

```
// Create the route query.
let query = HKWorkoutRouteQuery(route: myRoute) { (query, locationsOrNil, done, errorOrNil) in

    // This block may be called multiple times.

    if let error = errorOrNil {
        // Handle any errors here.
        return
    }

    guard let locations = locationsOrNil else {
        fatalError("*** Invalid State: This can only fail if there was an error. ***")
    }

    // Do something with this batch of location data.

    if done {
        // The query returned all the location data associated with the route.
        // Do something with the complete data set.
    }

    // You can stop the query by calling:
    // store.stop(query)

}
store.execute(query)
```

Note

Locations from the HealthKit store are accurate within 50 meters or fewer, but they may need additional smoothing before you can use them (for example, to produce clean lines when plotting the route on a map).

## See Also

### Route data

Creating a workout route

Record the user’s route during a workout.

class HKWorkoutRouteBuilder

A builder object that incrementally constructs a workout route.

class HKWorkoutRoute

A sample that contains a workout’s route data.

struct HKWorkoutRouteQueryDescriptor

A query interface that reads the location data stored in a workout route using Swift concurrency.

class HKWorkoutRouteQuery

A query to access the location data stored in a workout route.

let HKWorkoutRouteTypeIdentifier: String

A series sample containing location data that defines the route the user took during a workout.

class HKSeriesBuilder

An abstract base class for building series samples.

class HKSeriesSample

An abstract base class that defines samples that contain a series of items.

